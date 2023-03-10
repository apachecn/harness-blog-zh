# 24x7 服务卫士-您的产品卫士|安全带

> 原文：<https://www.harness.io/blog/harness-24-7-service-guard>

利用全天候服务保护就像开发人员有一个专门的保镖全天候监视他们的生产应用程序。如果有不好的事情发生，它会自动回滚代码更改并保护它们。

当 Harness 脱离隐身状态时，我们凭借几项独特的能力进入了[连续交付](https://harness.io/blog/what-is-continuous-delivery/)市场。我们的智能自动化帮助客户在几分钟内构建部署管道，我们的持续验证帮助开发人员自动验证和回滚他们的部署。

这就是我们如何帮助我们的前 35 个客户快速移动而不损坏东西的基本方法。

今天，我们宣布 24x7 服务保护，这基本上是类固醇的持续验证。

利用全天候服务保护就像开发人员有一个专门的保镖全天候监视他们的生产应用程序。如果有不好的事情发生，它会自动回滚代码更改并保护它们。

## 为什么要 24x7 服务卫士？

我们最初的持续验证集中在部署或金丝雀阶段，在新代码生命周期的前 15-20 分钟内分析新代码的性能/质量。客户可以定制这种验证持续时间，但它的范围总是有限的。这种能力在捕捉三分之二的性能异常和/或质量退化方面非常出色，因为大多数应用程序在部署后几分钟内就会失败。

创建 24x7 Service Guard 是为了捕捉新部署后数小时出现的异常/倒退。有时部署是在非工作时间完成的，此时应用程序的流量很小，或者用户可能无法立即访问或使用应用程序中的特定功能。

与此同时，我们的客户正在努力应对监控工具疲劳。他们拥有监控应用程序不同方面的一切。在微服务领域，一个客户可能有几十个微服务，有几十种不同的监控工具、日志和仪器。对开发人员和团队来说，统一这些数据集是一个巨大的挑战。

抓住部署后问题和工具疲劳是我们创建 24x7 Service Guard 的原因。我们希望为开发人员提供跨所有工具的生产应用的全面运营可见性，并在他们不注意时保护他们。

## 由无监督的机器学习提供动力

与持续验证一样，我们的 24x7 服务保护位于您所有 APM、监控和日志工具之上。然而，我们已经对我们的无监督机器学习进行了重大修改，以适应 24x7 数据流。

我们仍在使用核心算法，如符号聚合表示(SAX)和隐马尔可夫模型，但我们也应用了熵和几个新的神经网络，因此我们可以不断学习和检测未知的未知，并减少误报。[如果您想深入了解我们的人工智能/人工智能，请观看本次网络研讨会](https://www.youtube.com/watch?v=ZO5otWQ4PIc)。

Harness 使用 Harness 进行连续交付，因此我们已经对 24x7 Service Guard 进行了一段时间的测试，并对其准确性进行了数周的改进。

## 统一 APM、日志和可观察性数据

只需**注册您的工具的 URL、API/Webhook 和登录凭证，即可在几分钟内将一个或多个监控工具**添加到 Harness。

接下来，对于 Harness 中的每个应用程序，**为每个环境(开发、质量保证、试运行、生产)添加您想要的验证**，Harness 会解决剩下的问题。

设置完成后，点击顶部的**持续验证**导航选项卡，您会看到类似这样的内容:

从上面我们可以看到，24x7 Service Guard 正在保护 **Web 在线应用程序**，并且正在观察**生产环境的 4 个监控源(AppDynamics、Datadog、Splunk 和 Prometheus)** 。对于您启用了 24x7 Service Guard 的每个应用程序和[环境](https://harness.io/blog/deployment-environments/)，您将看到相同的视图。

一目了然，开发人员现在可以在几秒钟内观察到任何环境中任何监控工具的任何服务的健康状况。抱歉，失陪一下，但这真的很糟糕。我还没看到最精彩的部分。

用户可以从几个时间分辨率中进行选择:12 小时、1 天、7 天和 30 天。

根据 24x7 Service Guard 从每个监控工具观察到的数据，它将绘制每个时间段的服务运行状况热图。它还将显示和关联任何部署，以便用户获得全面的操作可见性。

## 了解服务和业务影响

交通灯是一种在高层次上理解服务健康的简单方法。有了 24x7 Service Guard，开发人员只需点击一下鼠标，就可以深入了解交通灯以外的服务对业务的影响。

例如，如果我们单击下面突出显示的红色时间片，我们会立即看到 AppDynamics 中受影响的业务事务以及以红色突出显示的相关异常/回归。

我们可以在下面看到交易**/在线/支付**正在经历高响应时间:

这种下钻功能的洞察力是由数据背后的监控工具的类型驱动的。例如，如果 Datadog 显示服务影响，24x7 Service Guard 将显示异常的云基础架构资源指标。如果 Splunk 正在显示影响，它将显示导致回归的错误或异常，等等。

可以把上面的内容看作是一种简单的方法，开发人员可以通过这种方法立即了解他们的监控数据集中发生了什么。

## 通过上下文追溯到根本原因

24x7 服务卫士不止于此。越来越好了。

Harness 还提供了上下文追溯，将开发人员从 Harness 带入他们正在进行故障诊断的指标或事件的上下文中的监控工具。

在上面的示例中，开发人员可以单击红色的 **/online/payment/** 交易，它会将他们直接带到异常的特定交易和时间段的 AppDynamics UI 中。

只需点击一下，你就可以从这个:

对此:

24x7 Service Guard 将为您喜爱的所有 APM 和日志工具提供同样的服务。

这一功能为开发人员提供了监控工具/数据的统一视图。它还允许他们只需点击几下鼠标就能找到根本原因。听起来简单，但功能极其强大。

## 自动回滚代码更改

24x7 Service Guard 的最后一个功能是在开发人员不注意时自动回滚代码更改(如果需要)。例如，让我们想象一个开发人员在一个星期五的下午 3 点使用 Harness 执行一个生产部署。经过 10-15 分钟的验证后，从性能和质量的角度来看，一切都很好。不久之后，开发商来到酒吧，喝了 5 品脱的吉尼斯黑啤酒。随着第五品脱吉尼斯黑啤酒的下肚，应用程序开始陷入停顿。24x7 Service Guard 会检测到这种性能异常，并作为预防措施，自动将应用程序回滚到其最后的工作状态。

开发人员第二天宿醉醒来，注意到前一天晚上来自 Harness 的警报。只需一次点击，开发人员就可以在性能异常的上下文中启动 Harness，并确定哪些事务负责，以及 APM 工具中性能问题的根本原因的链接。

## 支持的应用程序和工具

Harness 支持跨所有云提供商和裸机数据中心基础设施的非容器和容器化应用程序。

我们目前支持 AppDynamics、New Relic、Dynatrace、Datadog 和 Prometheus 的 APM 和时序指标。我们还有一个 API 来支持定制的时间序列数据。对于日志和事件数据，我们还支持 Splunk、Elastic/ELK、Sumo Logic、Bugsnag 和 Logz.io。

今天就注册你的[免费试用](https://app.harness.io/auth/#/signup)线束平台，给 24x7 服务卫士一个机会。