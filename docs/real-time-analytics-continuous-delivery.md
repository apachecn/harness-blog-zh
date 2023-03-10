# 持续交付的实时分析|利用

> 原文：<https://www.harness.io/blog/real-time-analytics-continuous-delivery>

分析与性感无关。在连续交付中有大量的领域需要分析，我们已经为您制作了一个漂亮的列表来帮助您。

根据维基百科， [**分析**](https://en.wikipedia.org/wiki/Analytics) 是数据中有意义模式的发现、解释和交流。供应商经常将这个术语与“饼图”混淆

分析是关于交流信息，这些信息与特定用户在特定用例中的上下文、理解和相关。在这种情况下，连续交货。

连续交货很难。自动化是一回事；理解它的影响或状态是另一个问题。一家大型零售商昨天告诉我，“我们有部署脚本，但一旦这些脚本在我们的应用程序和环境中执行，我们就缺乏任何可见性。”当您的 CI/CD 平台有 100 多个部署脚本时，可见性就变得非常困难。

我们的线束工程团队花了六个月的时间与客户合作，从零开始设计分析，以帮助他们管理 CD 管道。

这里是我们交付内容的快速总结。

## 部署速度分析

随着时间的推移，客户的部署速度是增加、减少还是持平？

在上面的例子中，您可以看到部署速度在过去两周内显著提高。在过去的一周里，失败也减少了。注意周末没人工作:)

## 服务速度分析

客户的哪些服务部署最频繁，这些部署管道中有多少实际上是成功的还是失败的？

看一眼上面的内容，就能立即告诉客户哪些服务部署得最多，更重要的是，哪些管道最容易成功或失败。CD 不仅仅是关于部署数量:有失败的管道是一件好事，因为它表明您实际上在最终用户之前就发现了问题。请记住，部署管道的目的是扼杀发布候选。

## 服务部署分析

现在每个服务的部署状态是什么？他们在什么环境中运行？这些环境有多大？目前部署了哪些版本？

给定服务的当前部署状态如何？

## 管道分析

每个部署管道的状态如何，所有管道阶段是否都成功完成？执行每个管道阶段需要多长时间？

## 部署工作流分析

部署管道中每个阶段和部署步骤的状态是什么？

上图是一个部署工作流的实时视图，允许开发团队观察他们的部署。单击任何工作流步骤都会提供关于状态和执行的详细信息(例如控制台日志)。

## 部署验证分析

每次部署都成功了吗？

每个部署给服务带来了哪些倒退或异常？下面的屏幕截图显示了一个部署引入了 5 个新的错误回归。突出显示的问题是由过期的无效 Docker 注册表凭据引起的。Harness 使用[无监督机器学习](https://harness.io/platform/continuous-delivery/continuous-verification/)技术来产生这种分析和洞察力。

每次部署对业务有何影响？下图显示了新部署为客户服务带来的 3 种新的性能回归。同样，我们将无监督的机器学习应用于第三方监控数据，以了解正常和异常的性能是什么样的。

## 安全性和合规性分析

谁在何时何地执行了什么？如何对每个部署管道、阶段、工作流、步骤和执行进行完整的审计跟踪，并完全访问控制台和日志文件？自动化仍然需要控制和标准的安全流程，尤其是对大型企业而言。

在所有部署管道中，有哪些秘密正在被管理、使用和更改？我们的客户想要一份完整的报告，报告他们的部署管道中使用和更改的所有机密。

## 分析不是为了性感

你可以让任何产品分析看起来很好，但真正的价值取决于用户能够多快理解并根据显示给他们的信息采取行动。具有简洁洞察力的简单视觉效果明显优于复杂视觉效果和信息过载。

使用 analytics，您不必一次回答多个问题——只需回答最常被问到的问题。当我们的工程师与客户坐在一起时，我们对连续交付时被问得最多的 10 个问题进行了排名。您在上面看到的只是一个开始，我们将在 2018 年交付更多内容！

如果您想评估 Harness，[注册我们的免费试用](https://harness.io/contact/)。
干杯！史蒂夫。@ BurtonSays 说