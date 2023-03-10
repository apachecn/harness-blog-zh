# 5 大 Java 日志框架| Harness

> 原文：<https://www.harness.io/blog/instrumentation-guide-application>

艰苦的工作永远不会结束，即使我们已经将应用程序交付给预期的用户，仍然有很多工作要做。现在我们需要看看我们的应用程序如何处理现实世界，并确保用户对此感到满意。输入仪器。

在接下来的文章中，我们将讨论插装的真正含义，以及可以帮助您将它作为应用程序的一部分来实现的各种选项和工具。我们走吧。

## 开发人员和运营人员相遇的地方

仪器是 DevOps 运动的关键属性之一，似乎每个人都在使用这个词，但它实际上意味着什么呢？

插装的字典定义是监视和测量性能、检测错误以及获取代表应用程序状态的跟踪信息的能力。就 DevOps 世界而言，监视和了解应用程序的状态和健康状况是非常准确的。

DevOps 背后有一个复杂的监控世界，其中包括注入代码以近距离监控它，找到正确的工具，并使用仪表板创建完整的视图，这将帮助我们了解“引擎盖下”发生了什么。

这就是仪器仪表如此重要的原因。这将有助于您在应用程序对您和您的用户造成混乱之前获得对它的洞察力。您需要知道您的应用程序中正在发生什么，并且您需要知道它在何时何地发生。那么，如何迈出第一步来检测您的应用呢？

几个月前，在 Monitorama 2016 大会上，Auth0 的基础设施产品负责人 James Fryman 展示了一种克服仪器仪表实施相关障碍的方法。

在他的演讲中，Fryman 提出了马斯洛需求层次的 DevOps 版本。层次结构的基础是文化，这意味着首先你必须准备好学习、失败、试验、集成和构建对你和你的应用有帮助的工具。

## 马斯洛需求层次理论的德文版本

只有在您知道您想要测量什么以及您计划如何测量之后，您才能开始理解应用程序的过程。您还需要了解 it 中涉及的技术和业务方面的流程。

一旦我们发现了自己的弱点，就该改进了。这就是插装与类、工具和对我们来说重要的所有东西的整体度量相结合的地方。重要的是确定在某一点上什么可能导致瓶颈，以及如何为我们和我们的用户提供更好的整体体验。

下一步包括同样的行动应该有同样的结果。可预见性。我们需要确保一切正常运行，以确保应用程序为我们的最终用户服务。

在金字塔中的改进和等幂步骤的几次迭代之后，我们想要确保我们的转换工作，并且我们可以保证 CD(连续部署)。Fryman 注意到，每个人都在争分夺秒地尽快到达那里，这导致沿着金字塔跳过了几步。

然而，如果我们想要一个给用户他们想要的发布周期，而不是一个修补以前的灾难的发布周期，那么经历每一个步骤和解决每一个“需求”是很重要的。

## 检测代码和日志

### 监控代码

大多数人更喜欢使用工具来实现插装，但这不是唯一可用的方法。如果您正在寻找一些更加 DIY 和动手处理代码的东西，Java 允许您添加监视代码本身的服务。您可以通过公共接口检测类来实现。

它提供了两种获取检测接口实例的方法:

1.  当 JVM 以指示代理类的方式启动时。在这种情况下，一个检测实例被传递给代理类的 premain 方法。
2.  当 JVM 提供了一种在 JVM 启动后的某个时间启动代理的机制时。在这种情况下，一个检测实例被传递给代理代码的 agentmain 方法。

一旦 Java 代理获得了插装实例，它就可以随时调用实例上的方法。我们可以使用可用的方法来测量和打印执行时间，返回 JVM 当前加载的所有类的数组，以及其他好的选项。

有两种代理——Java 和 Native。两者都以相似的方式加载到 JVM 中(JVM 启动参数)，但是它们的构建方式和实际功能不同。

在大多数情况下，我们更喜欢让商业工具来为我们处理代理。这就是 APMs 的用武之地。如果你正在寻找流行的 APM 工具，你可以看看我们对 AppDynamics 和 Dynatrace，或者 AppDynamics 和 New Relic 的比较。

### 守护进程

从我们的应用程序收集数据的另一个聪明的方法是通过守护进程，守护进程基本上是在后台运行的进程，从应用程序或底层系统收集数据。守护进程可以帮助我们更好地了解应用程序的状态和健康状况。

守护进程基于 4 个关键的架构点:信息的来源、它如何到达您的手中、数据将存储在哪里，以及您如何实际查看正在发生的事情。

有些守护进程要求您指定您希望在应用程序内部监视什么，而其他守护进程会为您获取信息，以防您不确定应该收集什么。

看看最流行的守护进程之一 StatsD，一个简单的 Node.js 应用程序帮助团队传输关于他们的网络、机器和应用程序的数据点，并将这些信息转换成图形，以便更好地了解正在发生的事情。

还有其他守护进程供您选择，每一个都有优缺点列表。如果您不确定哪一个适合您，请查看我们的 StatsD vs collectd vs fluentd 帖子，其中还包括一些您应该知道的其他守护程序。

### 日志管理

我们都知道，由于日志通常包含大量的信息，浏览日志就像在日志堆栈中找一根针，但要确切知道发生了什么并不总是容易的。这就是为什么日志管理工具在这里的救援。

这些工具为您提供了更好的数据视图，以及更好的搜索方式，而不是遍历成千上万的日志文件。这个领域有很多玩家，可能很难知道哪一个适合你。

为了帮助您了解谁对谁，我们为 Java 开发人员收集了 7 个日志管理工具的列表，您可以在这里阅读。我们还比较了市场上最大的两个工具，Splunk 和 ELK，以及游戏中其他一些玩家之间的比较。

然而，如果您正在寻找比日志管理工具提供更多上下文的东西，您可能想要尝试 OverOps。OverOps 从生产中抛出的错误和异常中捕获代码和变量数据，这意味着您可以知道代码在何时何地中断，而无需筛选日志文件。

## 抵制怎么办？

在他的演讲中，Fryman 提到了你在向你的团队推销仪器时可能会遇到的阻力。在大多数情况下，这是以前尝试过的东西，但在很短的时间内没有给出任何有用的反馈。

这里最重要的部分是迭代。工具化包括采取小而集中的步骤，从我们得到的信息中学习，并在下一个周期中实现它。即使是一点点改进或者只是少量数据，从长远来看也可能是一件大事。

改变是困难的，通常我们更喜欢避免改变看起来可行的东西，这就是为什么 Fryman 建议让所有的开发人员都参与进来并保持同步。它们可能是一个很好的反馈来源，将有助于建立一个更好的仪器仪表字流。

## 最后的想法

插装是关于测量我们在应用程序中需要和想要的一切，但这并不意味着我们必须实际测量所有可能的东西。我们必须明智地认识到我们的瓶颈可能是什么以及在哪里，并且专注于理解什么是重要的，如果它像它应该的那样工作的话。

改变我们已经习惯的工作流程是一项艰巨的工作，但为了给最终用户提供更好的应用程序和更好的体验，这是必要的。

除了这些工具，我们还收集了您在主要版本发布后应该使用的 15 个工具的列表，这些工具侧重于日志记录、性能监控、警报和跟踪，以及生产中的调试。