# 你应该知道的 5 个开源 APM 工具| Harness

> 原文：<https://www.harness.io/blog/5-open-source-apm-tools-you-should-know>

在本帖中，我们收集了一些目前可用的开源 APM 工具。

对于任何应用程序来说，最重要的事情之一就是性能。我们希望确保用户能够获得最好的体验，并知道我们的应用程序已经启动并运行。这就是为什么我们大多数人至少使用一种监控工具。

如果您正在性能监控市场中寻找稍微不同的东西，您可以选择的一个选项是使用开源工具。在下面的帖子中，我们收集了一些开源 APM 工具，这些工具现在可以作为付费工具的替代，所以你可以看看它是否是你的正确选择。

## 走向开源

APM 市场是一个拥挤的市场。你有著名的名字，比如 New Relic、AppDynamics(查看这篇文章对它们的概述)，还有 Dynatrace(我们在以前的文章中比较过)，以及一些较小或不太知名的工具。由于游戏中有如此多的玩家，并且他们都知道监控您的应用程序的价值，所以他们为自己保留了他们的代码。

然而，市场上有一个替代品:开源工具。如果您对在生产中获得应用程序可见性的简单方法感兴趣，或者如果您想知道您的代码实际上是如何被监控的，这些工具是一个很好的选择。

开源社区中也有一些关键的 APM 工具，每一个都有自己的产品和可能性。如果您感兴趣并想知道开源 APM 为您准备了什么，我们已经为您介绍了 5 大可用工具。

## 1.舞台监视器

Stagemonitor 提供了一个 Java 监控代理，它是根据集群应用程序栈构建的。这意味着它旨在监控运行在多个服务器上的应用程序。该工具集成了时间序列数据库(TSDB)。该工具针对处理时间序列数据以及按时间索引的数字数组进行了优化。这些数据库包括 Elasticsearch、Graphite 和 InfluxDB。

### 它是如何工作的？

Stagemonitor 包括一个位于 Java 应用程序中的代理，它向中央数据库发送指标和请求跟踪。该工具只需要一个实例来监控所有应用程序、实例和主机，并且可以部署在您自己的数据中心内。

在监控方面，您可以从集群或直接从 developer server 查看历史或实时数据，创建自定义警报并为每个指标定义阈值。

Stagemonitor 包括一个仪表板，因此您可以可视化和分析您感兴趣的不同指标和请求。您可以创建自定义仪表板，编写自定义插件，甚至使用第三方插件。它提供了一个无需后端的浏览器内小部件，可以自动注入到被监控的网页中。您可以通过以下链接观看现场演示。

在官方文档中，Stagemonitor 声明它也支持非基于 servlet 的应用程序，您可以在这里查看完整的需求。

一句话:如果你已经熟悉 ELK stack，它绝对值得一试。

## 2.精确的

Pinpoint 是为大规模分布式系统设计的 APM 工具。它模仿 Dapper，一个由 Google 构建的分布式系统跟踪基础设施，为其开发人员提供更多关于复杂分布式系统行为的信息。

### 它是如何工作的？

该工具通过跟踪跨分布式应用程序的事务，帮助分析系统的整体结构以及其中的组件是如何相互连接的。这意味着它旨在解释每个事务是如何执行的，跟踪组件之间的流程，以及(前面的坏笑话)指出有问题的领域和潜在的瓶颈。

仪表板有助于可视化组件的连接方式，并允许您实时监控应用程序内部的活动线程。Pinpoint 还允许您查看请求计数和响应模式，以便您能够识别潜在的问题。您可以查看关键的详细信息，包括 CPU 使用率、内存/垃圾收集和 JVM 参数。

Pinpoint 与无需任何代码更改就可以安装的代理一起工作，您可以在自己的机器上运行一个示例实例，方法是为每个组件运行四个简单的脚本:Collector、Web、Sample TestApp 和 HBase。

一句话:如果您听说过 Dapper，或者想要监视和分析您复杂的分布式系统，您绝对应该看看这个工具。

## 3.莫斯基托

MoSKito 提供三合一工具:

1.  moski to-Essential–基本的独立项目。它是 MoSKito 功能的核心，让您可以监控您的应用程序
2.  moski to-Central–用于保存性能数据的中央存储服务器
3.  moski to-Control——一个监控多节点 web 应用程序性能的工具

### 它是如何工作的？

要开始，您只需放下。jar 文件放入 WEB-INF/lib 文件夹，或者在 web.xml 文件中包含一个新的小部分。一旦该工具启动并运行，它就会收集性能数据，对其进行实时分析，并将其存储起来用于历史分析。

该工具收集您的所有性能指标，如线程、内存、缓存、存储、服务、注册、支付、转换、SQL、负载分布等。它不需要修改代码，支持所有主要的应用服务器(Tomcat、Jetty、JBoss、WebLogic)，并将数据保存在本地。

您还可以获得一个通知系统来了解何时达到阈值，以及您想要监控的用户操作的记录。除了基于 web 的仪表盘，该工具还提供了一个移动应用程序，可随时监控您的应用。

一句话:MoSKito 于 2007 年首次推出，现在它是一个众所周知的稳定工具，受到团队和社区的支持，包括付费支持选项。这对任何开源工具来说都是一个巨大的优势。

## 4.格洛鲁特

Glowroot 以其快速、干净和简单的 APM 工具而自豪。它将允许对缓慢的请求和错误进行跟踪捕获，并且您将能够记录每个用户操作的时间跟踪，以及 SQL 捕获和聚合。该工具还提供了所有数据的历史汇总，并具有可配置的保留期。

它提供了可视化响应时间分解和响应时间百分比的图表，它的响应 UI 将允许您从移动设备和桌面监控您的应用程序。

### 它是如何工作的？

要开始使用 Glowroot，需要下载并解压缩主安装文件，并将-Java agent:path/to/glow root . jar 添加到应用程序的 JVM 参数中。启动应用程序后，剩下的就是将浏览器指向 http://localhost:4000。

一旦该工具启动并运行，您将获得连续的概要分析(带有过滤选项)，并能够设置响应时间百分比和 MBean 属性的警报。Glowroot 完全支持跨多线程的异步请求，它支持 Tomcat、TomEE、JBoss EAP、Wildfly、Jetty 和 Glassfish。

底线:如果干净和简单是你正在寻找的，毫无疑问你会想看看 Glowroot 而不是这里的其他工具。

## 5.卡蒙

Kamon 是一个反应友好的工具包，为运行在 JVM 之上的应用程序而构建。更具体地说，它是为使用类型安全反应平台(使用 Scala、Akka、Spray 和/或 Play！)，但仍然支持任何其他 JVM 平台和语言。

### 它是如何工作的？

Kamon 作为一个核心模块发布，包含所有的度量记录和跟踪操作 API 以及可选模块，为您的应用程序提供字节码工具和/或报告功能。或者换句话说，它提供了一个简单的 API 来记录度量和跟踪 JVM 应用程序的信息。

Kamon 的所有模块都可以通过 Maven Central 获得，您需要将它们作为编译依赖项添加到您的项目中。一旦你包含了你感兴趣的模块，只需启动 Kamon，所有可用的模块将自动启动，你不需要显式激活/启动它们。

跟踪模块将允许记录关于在您的应用程序中执行的功能的数据，度量模块将允许您控制由用户代码或由其他 Kamon 模块提供的工具跟踪的实体的注册。它还具有其他功能，如过滤、配置仪器工厂和调度指标订阅。

一句话:如果你正在使用多种 JVM 语言，或者主要是 Scala / Akka，并且想要“一个工具来监控它们”，Kamon 可能是最友好的选择。

## 现在你已经有了你的干草堆…

APM 工具可以很好地为您提供关于您的应用程序是否已经启动并运行，或者是否有什么东西在阻碍它的信息。唯一的问题是，一旦你找到了发现问题的那个干草堆，你就必须开始四处挖掘，寻找导致问题的真正的针头。

与其筛选日志文件试图找出哪里出了问题，在哪里发生的，以及可能是什么原因造成的，不如有一个更好的解决方案。OverOps 不仅会向您提供何时何地发生错误的答案，还会向您展示错误发生的原因——为您提供整个调用堆栈中导致错误的完整源代码和变量状态。看看这个。

## 最后的想法

在 APM 领域，这些是付费工具的很好的替代品。但是……有些人可能认为选择开源软件是省钱的好方法。同样重要的是要记住，虽然你不需要为使用该工具开具发票，但这并不一定意味着它更便宜。

开源工具是有代价的:安装、故障排除，当然还有维护，这些都将在内部完成，由您自己的工程师甚至您来完成。更不要说你可能会浪费时间去为一个只有你遇到过，而社区从未听说过的特定问题寻求支持。

我们的两美分是，开源可以是伟大的，但你也应该记住其他成本，然后才作出决定。

你认为我们还应该看看其他开源 APM 工具吗？在下面的评论中告诉我们吧！