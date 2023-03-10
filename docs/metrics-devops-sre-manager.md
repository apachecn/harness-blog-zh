# 任何开发人员和 SRE 经理都必须衡量的指标|管理

> 原文：<https://www.harness.io/blog/metrics-devops-sre-manager>

为了了解每个公司内部发生了什么，我们需要衡量 DevOps 和 SRE 团队的表现。

DevOps 和 sre 拥有监控服务和产品绩效的仪表板，现在是时候让我们了解如何衡量这些团队的绩效了。

如今，每家公司面临的一个重大挑战是衡量。有必要了解公司和产品内部每个层面发生的事情，从客户如何使用应用程序，到代码的质量和效率，再到团队的表现。

当谈到衡量 DevOps 和 SRE 团队时，我们面临着一个全新的挑战。他们负责传递漏斗，他们的工作是测量并确保它正常工作。从编写代码的开发人员，到测试和部署代码的工具，再到产品在现实世界中的行为方式。

虽然 DevOps 和 SREs 测量性能，确保应用程序生命周期中的每一步都正常运行，但我们需要了解如何反过来测量它们。我们告诉你这是一个挑战，但我们也有一些好消息——这是可能的，只要你专注于重要的事情。

## 我们应该衡量什么？

DevOps 和 SREs 必须掌握应用程序内部发生的一切。他们需要一个实时监控系统，这将有助于他们了解应用正常运行时间、加载时间、API 调用的数量和成功、CPU 进程线程、内存使用情况和其他指标。虽然确保一切正常运行是他们的工作，但我们希望确保他们按预期行事。为此，我们还需要查看整个应用程序和工作流，以找到我们感兴趣的每个参数的答案和数据。
这些通常包括:

*   我们希望通过查看周期时间来确保开发团队比以前交付得更快。
*   我们需要知道**快速部署**不会损害代码的质量，这可以通过产品的可用性来衡量。
*   我们希望通过查看回滚百分比来监控**产品的质量**。
*   当然，我们希望确保我们的**用户和客户满意**，这可以通过查看回滚百分比或发送的投诉来实现。

这些参数中的每一个都包含大量的指标和计算，试图监控所有这些参数就像试图在 7 月 4 日拍摄整个烟花表演一样:你可以做到，但你错过了重点。

为了帮助我们自助，我们需要缩小我们所看到的范围。由于我们的目标是衡量我们自己的团队和运营，因此更容易退一步，从更广阔的角度审视一切。现在，让我们将这些类比转化为实践。

## 借用谷歌的焦点

DevOps 和 SREs 必须监控应用程序的许多不同方面，但这并不意味着我们也需要监控其中的每一个方面。此外，这并不意味着我们需要许多仪表板来了解团队是否在做他们的工作。

为了缩小范围，我们可以采用谷歌的方法来衡量其 SRE 团队。该公司将监测 DevOps 和 SRE 所需的所有元素封装到三个基本测量中，每个测量都有自己的基线:

### 服务水平目标(SLO)

在 Google 中，服务水平目标(SLO)是一个表示系统可用性的数字或百分比。这表明系统是否正常运行，以及产品是否稳定。

这个数字将帮助我们了解产品的状态和质量，并在我们加快部署时确保代码的质量。开发运维团队和 SRE 团队的部分职责是维护应用程序的可靠性和功能性。该指标清楚地代表了团队在实现该目标方面的成功程度。

### 服务水平指示器(SLI)

此指标通过计算请求延迟、每秒请求吞吐量或一段时间内每个请求的失败次数来衡量每个请求的失败次数。它连接到确定的 SLO 数，并帮助评估团队是否在其 SLO 内。

有了对系统可用性等指标的可见性，就更容易理解错误和故障何时发生。合乎逻辑的下一步是找出导致错误和失败的原因。这将使我们能够监控我们的服务的可靠性，我们将能够通过查看 DevOps 和 SRE 团队正在测量的相同统计数据来做到这一点。

### 服务水平协议

服务水平协议(SLA)是您和您的用户/客户之间的协议，表明服务和产品的可用性。与 SLO 和 SLIs 不同，这是一个松散的指标，可以根据您提供的服务或您提供服务的客户而变化。

SLA 应该从 SLO 中派生出来，因为您希望在与客户签订合同和承诺之前，确保您对系统可用性有自己的定义和理解。从衡量标准的角度来看，监控 SLA 将有助于我们了解 DevOps 和 sre 是否跟上了他们为自己设定的数字。

## 最后的想法

你希望你的产品是好的，你的顾客是快乐的，你的公司是成功的。但是如果不附上正确的数字和度量标准，你怎么知道你是否在正确的轨道上呢？

理解如何监控 DevOps 和 SREs 是一个挑战，但您需要能够衡量作为您产品一部分的所有东西，而这些团队是其中的一大部分。

虽然每个公司都有自己的一套要求、方法和团队结构，但是专注于监控 SLO、sli 和 SLA 将有助于您了解应该关注哪些指标，以及您的团队表现如何。