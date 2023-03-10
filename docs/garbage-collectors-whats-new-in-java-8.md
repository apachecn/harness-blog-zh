# 垃圾收集器–串行与并行、CMS 与 G1(以及 Java 8 中的新特性)| Harness

> 原文：<https://www.harness.io/blog/garbage-collectors-whats-new-in-java-8>

了解 Java 8 中不同类型的垃圾收集器。

垃圾收集是众所周知的影响性能的事情之一，但除此之外，就其实际工作方式而言，它对我们大多数人来说都是一个谜。因此，我们认为我们应该尽力介绍 GC 的基础知识，特别是因为这是一个 Java 8 已经经历了一些重大变化和改进的领域，尤其是删除了 PermGen 和一些令人兴奋的新优化(在最后会有更多相关内容)。

当我们谈到垃圾收集时，大多数人都知道这个概念，并在日常编程中使用它。即便如此，还有很多我们不了解的地方，这就是事情变得痛苦的时候。对 JVM 最大的误解之一是它只有一个垃圾收集器，而实际上它提供了四个不同的垃圾收集器，每个都有自己独特的优点和缺点。选择使用哪一个并不是自动的，而是由您自己决定的，吞吐量和应用程序暂停之间的差异可能会很大。

这四种垃圾收集算法的共同点是它们是分代的，这意味着它们将托管堆分成不同的段，使用了古老的假设，即堆中的大多数对象都是短期的，应该快速回收。由于这也是一个广泛讨论的领域，我将直接进入不同的算法，以及它们的优缺点。

## **1。串行收集器**

串行收集器是最简单的，也是您可能不会使用的，因为它主要是为单线程环境(例如 32 位或 Windows)和小堆设计的。这个收集器在工作时会冻结所有应用程序线程，这使得它在任何情况下都不能在服务器环境中使用。

使用方法:打开 *-XX:+UseSerialGC* JVM 参数就可以使用

## **2。并行/吞吐量收集器**

下一个是并联集电极。这是 JVM 的默认收集器。就像它的名字一样，它最大的优点是使用多线程来扫描和压缩堆。并行收集器的缺点是，当执行少量或全部 GC 收集时，它会停止应用程序线程。并行收集器最适合能够容忍应用程序暂停并试图优化收集器导致的较低 CPU 开销的应用程序。

## **3。CMS 收集器**

并行收集器的后续是 CMS 收集器(" *concurrent-mark-sweep* ")。该算法使用多线程(“并发”)在堆中扫描(“标记”)可以回收的未使用的对象(“清除”)。该算法将在两种情况下进入“停止世界”(STW)模式:当初始化根(从线程入口点或静态变量可到达的老一代中的对象)的初始标记时，以及当应用程序在算法同时运行时改变了堆的状态时，迫使它返回并做一些最后的修改以确保它标记了正确的对象。

使用这个收集器时，最大的问题是遇到**提升失败**，这是收集年轻代和老代之间发生竞争情况的实例。如果收集器需要将年轻对象提升到老一代，但没有足够的时间来腾出空间，它将必须首先这样做，这将导致完整的 STW 收集-这正是 CMS 收集器想要阻止的事情。为了确保这种情况不会发生，您可以增加老一代的大小(或者整个堆的大小)，或者为收集器分配更多的后台线程，以便与对象分配的速率竞争。

与并行收集器相比，此算法的另一个缺点是它使用更多的 CPU，以便通过使用多线程来执行扫描和收集，从而为应用程序提供更高级别的连续吞吐量。对于大多数不利于应用程序冻结的长期运行的服务器应用程序，这通常是一个很好的折衷。即便如此，这个算法也是**默认**不开启。你必须指定 *XX:+USeParNewGC* 来启用它。如果您愿意分配更多的 CPU 资源来避免应用程序暂停，这是您可能想要使用的收集器，假设您的堆小于 4Gb。然而，如果它大于 4GB，您可能希望使用最后一种算法——G1 收集器。

## **4。G1 收藏家**

JDK 7 update 4 中引入的垃圾优先收集器(G1)旨在更好地支持大于 4GB 的堆。G1 收集器利用多个后台线程来扫描它划分成区域的堆，范围从 1MB 到 32MB(取决于堆的大小)。G1 收集器首先扫描那些包含最多垃圾对象的区域，并给它起了个名字(垃圾优先)。使用*–XX:+use G1 GC*标志打开该收集器。

这种策略降低了在后台线程完成扫描未使用的对象之前耗尽堆的可能性，在这种情况下，收集器将不得不停止应用程序，这将导致 STW 收集。G1 还有另一个优点，那就是它可以随时压缩堆，这是 CMS 收集器仅在完整 STW 收集期间才会做的事情。

在过去的几年里，大型堆一直是一个颇有争议的领域，许多开发人员从每台机器一个 JVM 模型转向每台机器多个 JVM 的更微服务、组件化的架构。这是由许多因素驱动的，包括希望隔离不同的应用程序部分、简化部署和避免通常将应用程序类重新加载到内存中所带来的成本(这在 Java 8 中实际上已经得到了改进)。

即便如此，对于 JVM 来说，这样做的最大驱动力之一是希望避免那些长时间的“停止世界”暂停(在大型集合中可能需要几秒钟)，这种暂停发生在大型堆中。Docker 之类的容器技术也加速了这一过程，使您能够相对容易地在同一台物理机上部署多个应用程序。

## **Java 8 和 G1 收集器**

Java 8 update 20 刚刚推出的另一个漂亮的优化是 G1 收集器**字符串重复数据删除**。由于字符串(及其内部 char[]数组)占用了我们堆中的大部分空间，因此我们进行了一项新的优化，使 G1 收集器能够识别在整个堆中重复多次的字符串，并将其更正为指向同一个内部 char[]数组，以避免同一字符串的多个副本低效地驻留在堆中。您可以使用*-XX:+UseStringDeduplication*JVM 参数来尝试一下。

## **Java 8 和 PermGen**

Java 8 中最大的变化之一是[移除了](http://java.dzone.com/articles/java-8-permgen-metaspace)堆中传统上为类元数据、内部字符串和静态变量分配的 permgen 部分。传统上，这需要开发人员使用会加载大量类的应用程序(使用企业容器的应用程序中常见的东西)来专门针对堆的这一部分进行优化和调优。多年来，这已经成为许多内存异常的来源，所以让 JVM(主要)注意这是否是一个非常好的添加。即便如此，这本身可能不会减少开发人员将其应用程序解耦到多个 JVM 中的趋势。

这些收集器中的每一个都通过一系列切换和开关进行了不同的配置和调整，每个都有可能增加或减少吞吐量，所有这些都基于您的应用程序的特定行为。我们将在接下来的文章中深入探讨配置这些的关键策略。