# 生产 Java 应用程序中的 10 大异常类型——基于 1B 事件|利用

> 原文：<https://www.harness.io/blog/10-exception-types-in-production-java-applications>

了解生产 Java 应用程序中的 10 大异常以及如何避免它们。

**帕累托记录原则:97%的记录错误语句是由 3%的独特错误引起的**

在最近的数据处理帖子中，我们发现 97%的记录错误是由 10 个独特的错误引起的，随后我们收到了很多反馈和问题。根据大众的需求，我们将深入研究这项研究中包含的一千多个应用程序中的顶级异常类型。
‍

我们走吧。

## 事不宜迟:按类型排列的顶级异常

为了提取数据，我们分析了由 Harness Service Reliability Management 的错误分析微代理监控的一千多个应用程序的匿名统计数据，并检查了每个公司的前 10 大异常类型。然后我们综合所有的数据，得出了整体的前 10 名名单。

‍
每个生产环境都是不同的，研发团队使用不同的第三方库，也有他们自己定制的异常类型。从更大的角度来看，标准的例外很突出，一些有趣的模式变得清晰可见。

## 1.NullPointerException–70%的生产环境

是的。臭名昭著的 NullPointerException 位于第一位。零引用的发明者查尔斯·安东尼·理查德·霍尔爵士说得没错:“我称之为我的十亿美元错误。这是 1965 年零引用的发明…这导致了无数的错误、漏洞和系统崩溃，在过去的四十年里，这可能造成了十亿美元的痛苦和损失。”

‍
在我们调查的 70%的生产环境中，npe 都排在前 10 位，占据首位。在 Harness，我们实际上有一个特殊的警报，让我们知道什么时候在我们的系统上引入了一个新的 NullPointerException。

## 2.NumberFormatException–55%的生产环境

在 at #2 中是 NumberFormatException，当您试图将一个字符串转换为一个数值，而该字符串的格式不正确时，就会发生这种情况。它扩展了 IllegalArgumentException，它也出现在#3 中。

‍
一个简单的方法可以确保你传递给解析方法的输入通过这些正则表达式:

1.  对于整数值:"-？\\d+"
2.  对于浮点值:"-？\\d+。\\d+"

## 3.非法参数异常–50%的生产环境

接下来排在第三位的是 IllegalArgumentException，它出现在本次调查中 50%的生产环境中的前 10 个异常中。一个 IllegalArgumentException 实际上把你从麻烦中解救出来，当你把一个意外类型的参数传递给你的方法时抛出。例如，某个需要 X 类型的方法，你用 Y 类型作为参数来调用它。这又是一个错误，它是由于没有检查作为其他方法输入的内容而导致的。

## 4.运行时异常–23%的生产环境

前 10 个列表中的所有异常对象(除了 exception)都是未检查的，并扩展 RuntimeException。然而，在第四点，我们面临一个“纯粹的”运行时异常，Java 语言本身实际上并不抛出任何异常。这是怎么回事？从代码中显式抛出 RuntimeException 主要有两种情况:

1.  抛出一个新的“通用”未检查异常
2.  重新抛出:
3.  将一个通用的未检查异常“包装”在另一个扩展 RuntimeException 的异常周围
4.  取消选中已选中的异常

[关于检查与未检查的一个著名故事](http://docs.aws.amazon.com/AWSSdkDocsJava/latest/DeveloperGuide/java-dg-exceptions.html)我们在这里描述的最后一个用例来自亚马逊的 AWS SDK，它只抛出未检查的异常，拒绝使用检查的异常。

## 5.IllegalStateException–22%的生产环境

排在第五位的是 IllegalStateException，在本帖涵盖的 1000 多个应用程序中，有 22%出现在前 10 个异常中。当你试图在不恰当的时间使用一个方法时，会抛出一个 IllegalStateException。

‍
一个更现实的 Java 例子是，如果你使用 URLConnection，试图做一些假设你没有连接的事情，并得到“IllegalStateException:已经连接”。

## 6.NoSuchMethodException–16%的生产环境

[这样的方法，多混乱](https://i.imgflip.com/1568ov.jpg)。在这次数据危机中，16%的生产环境的前 10 名中都有 NoSuchMethodException。
因为我们大多数人不会在喝醉的时候写代码，至少在白天，这并不意味着我们会神志不清地认为我们看到了不存在的东西。那样的话，编译器会在进程的早期发现这种情况。

‍
当你试图使用一个不存在的方法时，这个异常被抛出，当你使用反射并从某个变量获得方法名时，或者当你构建一个类的版本并在生产中使用一个不同的版本时，就会发生这种情况(感谢 [@braxuss](https://twitter.com/braxuss) )。

## 7.ClassCastException–15%的生产环境

当我们试图将一个类强制转换为另一个不是实例的类时，就会发生 ClassCastException。15%的生产环境在其前 10 个异常中有它，相当麻烦。

‍
规则是你不能将一个对象强制转换成一个它没有继承的不同的类。大自然在无人注意的时候做了一次，这就是我们如何得到… [爪哇鼠鹿](https://en.wikipedia.org/wiki/Java_mouse-deer)。是的，那是一个真实的生物。

## 8.例外–15%的生产环境

at #8 是所有异常之母。Java 从不抛出普通的异常，所以这是另一种类似 RuntimeException 的情况，它必须是…你或第三方代码，因为:

1.  你需要一个异常，只是懒得具体说明它到底是什么。
2.  或者……更具体地说，出于某种原因，您需要抛出一个检查过的异常

## 9.parse exception–13%的生产环境

解析错误再次来袭！每当我们传递一个字符串来解析成其他的东西，并且它没有按照预期的方式格式化，我们就会遇到 ParseException。真扫兴。

‍
这比你想象的要普遍得多，在这篇文章中测试的生产环境中，有 13%在它们的前 10 名中出现了这种异常。
解决方法是…再次检查你自己。

## 10.InvocationTargetException–13%的生产环境

另一个来自 Java 反射世界的异常是 InvocationTargetException。这实际上是一个包装器，如果在一个被调用的方法中出错，那么这个异常就用一个 InvocationTargetException 包装起来。

‍
要获得原始异常，你必须使用 getTargetException 方法。

‍
我们看到，在这篇文章中测试的生产环境中，有 13%在其 10 大异常列表中。这里的第二种异常类型与 Java 的反射特性直接相关。

## 最后的想法

Java 异常的世界确实是丰富多彩的，看到前 10 个异常对我们的日志有如此大的影响真是令人惊讶。所有记录的错误中有 97%来自 10 个独特的异常。

‍
尝试利用服务可靠性管理，找出你自己生产环境中的 10 大异常。只需要几分钟就可以开始，而且你还可以获得修复它们所需的所有数据。源、堆栈、状态。