# 关于 Java 和 Scala | Harness 中的同步，你不知道的 5 件事

> 原文：<https://www.harness.io/blog/5-things-synchronization-java-scala>

让我们探索最同步的习语——对象锁。

几乎所有的服务器应用程序都需要多线程之间的某种同步。大部分同步工作是在框架级别上为我们完成的，比如通过我们的 web 服务器、DB 客户端或消息传递框架。Java 和 Scala 提供了大量组件来编写可靠的多线程应用程序。这些包括对象池、并发集合、高级锁、执行上下文等..

为了更好地理解这些，让我们来探索最同步的习语——对象锁。这种机制为 synchronized 关键字提供了动力，使其成为 Java 中最流行的多线程习语之一。它也是我们使用的许多更复杂模式的基础，比如线程和连接池、并发收集等等。

synchronized 关键字主要用于两种情况:

*   作为方法修饰符来标记一个方法，该方法一次只能由一个线程执行。
*   通过将一个代码块声明为一个临界区——一个在任何给定的时间点只对单个线程可用的临界区。

## 锁定说明

### 事实#1

同步代码块使用两个专用字节码指令实现，这是官方规范的一部分——monitor enter 和 MonitorExit。这不同于其他锁定机制，例如 java.util.concurrent 包中的那些机制，这些机制是使用 java 代码和通过 sun.misc.Unsafe 进行的本机调用的组合来实现的(在 HotSpot 的情况下)

这些指令对开发人员在同步块的上下文中明确指定的对象进行操作。对于同步方法，锁被自动选择为“this”变量。对于静态方法，锁将放在类对象上。

同步方法有时会导致不良行为。一个例子是在同一对象的不同同步方法之间创建隐式依赖关系，因为它们共享同一个锁。更糟糕的情况是在基类(甚至可能是第三方类)中声明同步方法，然后将新的同步方法添加到派生类中。这在整个层次结构中创建了隐式的同步依赖，并有可能造成吞吐量问题甚至死锁。为了避免这些，建议使用私人持有的对象作为锁，以防止锁的意外共享或逃脱。

[adrotate group="11 "

#### 编译器和同步

有两个字节码指令负责同步。这是不寻常的，因为大多数字节码指令是相互独立的，通常通过将值放在线程的操作数堆栈上来相互“通信”。要锁定的对象也从操作数堆栈中加载，通过解引用变量、字段或调用返回对象的方法预先放置在那里。

### 事实 2

那么，如果调用两个指令中的一个，而没有分别调用另一个，会发生什么呢？Java 编译器不会生成调用 MonitorExit 而不调用 MonitorEnter 的代码。即便如此，从 JVM 的角度来看，这样的代码是完全有效的。这种情况的结果将是 MonitorExit 指令抛出 IllegalMonitorStateException。

更危险的情况是，如果通过 MonitorEnter 获得锁，但没有通过相应的 MonitorExit 调用释放锁，会发生什么情况。在这种情况下，拥有锁的线程可能会导致试图获取锁的其他线程无限期地阻塞。值得注意的是，由于锁是可重入的，所以拥有锁的线程可以继续愉快地执行，即使它再次到达并重新进入同一个锁。

这就是问题所在。为了防止这种情况发生，Java 编译器以这样的方式生成匹配的进入和退出指令，即一旦执行进入同步块或方法，它必须为同一对象传递匹配的 MonitorExit 指令。有一件事可能会造成这种情况，那就是如果在临界区抛出了异常。

###### [Java]
public void hello(){
synchronized(this){
system . out . println(" Hi！，我一个人在这里”)；
}
}
[/java]

让我们来分析字节码——

###### 【Java】
aload _ 0//将此加载到操作数堆栈
dup//再次加载
astore _ 1//将此备份到存储在寄存器 1 的隐式变量中
monitor enter//从堆栈中弹出此的值进入监视器
//实际临界区
get static Java/lang/System/out Ljava/io/PrintStream；
ldc“嗨！，我一个人在这里"
invokevirtual Java/io/PrintStream/println(Ljava/lang/String；)V
a load _ 1//加载此
监视器的备份 exit 弹出 var 并退出监视器
goto 14//completed–跳转到结尾
//添加的 catch 子句–如果抛出异常我们就到了这里—
a load _ 1//加载备份 var。
monitor exit//退出监视器
at row//重新抛出异常对象，加载到操作数堆栈
返回
[/java]

编译器用来防止堆栈在没有通过 MonitorExit 指令的情况下展开的机制非常简单——编译器添加了一个隐式 try…catch 子句来释放锁并重新抛出异常。

### 事实#3

另一个问题是在相应的进入和退出调用之间存储的对锁定对象的引用在哪里。请记住，多个线程可以使用不同的锁对象同时执行同一个同步块。如果锁定的对象是方法被调用的结果，那么 JVM 不太可能再次执行它，因为它可能会改变对象的状态，甚至可能不会返回同一个对象。对于自进入监视器以来可能已经改变的变量或字段，情况也是如此。

监视器变量。为了解决这个问题，编译器在方法中添加了一个隐式局部变量来保存锁定对象的值。这是一个聪明的解决方案，因为与使用并发堆结构将锁定对象映射到线程(这种结构本身可能需要同步)相比，它在维护对锁定对象的引用上施加了相当小的开销。我第一次观察这个新变量是在构建 OverOps 的堆栈分析算法时，发现代码中出现了意想不到的变量。

注意，所有这些工作都是在 Java 编译器级别完成的。JVM 非常乐意通过 MonitorEnter 指令进入临界区而不退出(反之亦然)，或者使用不同的对象作为相应的进入和退出方法。

#### 在 JVM 级别锁定

现在让我们更深入地看看锁在 JVM 级别上是如何实现的。为此，我们将研究 HotSpot SE 7 实现，因为这是特定于 VM 的。由于锁定会对代码吞吐量产生一些非常不利的影响，JVM 进行了一些非常强大的优化，以尽可能高效地获取和释放锁。

事实四。JVM 提供的最强大的机制之一是线程锁偏置。锁定是每个 Java 对象的固有功能，就像拥有一个系统 hashcode 或对其定义类的引用一样。不管对象的类型如何，这都是正确的(如果愿意，您甚至可以使用一个原始数组作为锁)。

这些类型的数据存储在每个对象的头中(也称为对象的标记)。放在对象头中的一些数据是为描述对象的锁定状态而保留的。这包括描述对象锁定状态(即锁定/解锁)的位标志，以及对当前拥有锁的线程的引用——线程偏向对象。

为了节省对象头中的空间，Java 线程对象被分配在 VM 堆的较低部分，以便减少地址大小并节省每个对象头中的位(64 位和 32 位 JVM 分别为 54 位或 23 位)。

#### 锁定算法

当 JVM 试图获取一个对象的锁时，它会经历一系列的步骤，从乐观到悲观。

### 事实 5

如果线程成功地将自己确立为对象锁的所有者，则它获得锁。这取决于线程是否能够在对象头中安装对自身的引用(指向内部 JavaThread 对象的指针)。

第一次尝试是使用简单的比较和交换(CAS)操作。这是非常有效的，因为它通常可以翻译成直接的 CPU 指令(例如 cmpxchg)。CAS 操作以及特定于操作系统的线程驻留例程充当对象同步习语的构建块。

如果锁是自由的或者先前已经偏向该线程，则为该线程获得对象上的锁，并且执行可以立即继续。如果 CAS 失败，JVM 将执行一轮旋转锁定，线程将在两次重试 CAS 之间有效地进入睡眠状态。如果这些初始尝试失败(表示对锁的争用程度相当高)，该线程会将自己移动到阻塞状态，并在争用锁的线程列表中排队，并开始一系列自旋锁。

打开锁。当通过 MonitorExit 指令退出临界区时，所有者线程将尝试查看是否可以唤醒任何可能正在等待锁被释放的已暂停线程。这个过程被称为选择“继承人”。这是为了增加活动性，并防止线程在锁已经被释放的情况下仍然处于暂停状态(也称为搁浅)。

调试服务器多线程问题很难，因为它们往往依赖于非常具体的时间和操作系统启发。这也是我们开始行动的原因之一。