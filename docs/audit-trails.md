# 什么是审计追踪&为什么你需要它们在 CD | Harness 中

> 原文：<https://www.harness.io/blog/audit-trails>

审计线索，也称为审计日志，是一组按时间顺序排列的记录，提供书面证据。审计追踪的目的可以用来跟踪特定的事件、操作或程序。

根据你在职业和技术旅程中所处的位置，“审计”这个词会引发不同的情绪。如果你以前没有经历过 IT 审计，你可能会想到一个浪漫的想法，几个外部审计员在一个会议室里仔细研究打印的系统日志。尽管在技术领域，理解什么、在哪里、为什么以及如何发生变化每天都很重要——不仅仅是在年度审计期间。

在技术世界里，与多个系统打交道既是一件好事，也是一件坏事。潜在的可能性是，拥有所发生事情的电子记录似乎更容易系统地产生。然而，系统很少以相同的方式修改，拼凑出发生了什么变化以及如何发生变化看起来像是一门法医学课程。不管是哪个行业，拥有审计跟踪或审计日志对所有组织都有好处。

## 什么是审计追踪？

审计线索，也称为审计日志，是一组按时间顺序排列的记录，提供书面证据。审计追踪的目的可以用来跟踪特定的事件、操作或程序。例如，你的杂货店收据可以作为你购物的记录。在财务记录中，您的分类帐或交易集合是审计线索。

应用生命周期管理(ALM)实践已经存在一段时间了。一种常见的开发实践是将需求/缺陷/变更请求与修改的代码联系起来。例如，在现代实践中，这看起来像是一个与 JIRA 票或 GitHub 问题相关联的[拉请求](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)。这只是故事的一部分。当进入生产阶段时，你的[连续交付](https://harness.io/blog/continuous-delivery/what-is-continuous-delivery/)管道不仅对编排应用程序代码变更至关重要，对基础设施和发布策略也是如此。

## 审计跟踪在持续交付中的优势

导航软件交付是包含软件整个生命周期的决策和变更的顶点；很少有一个工程师在其整个职业生涯中参与一个项目。解释变更可能是非常部落化的，并且对解释开放，特别是如果那些创建和/或做出变更的人已经离开了团队。

由于现代组织利用他们的连续交付管道作为生产的核心管道，实施变更的系统在成为变更的系统记录方面非常出色。

### 系统记录系统

取决于你喜欢或不喜欢在学校记笔记，当人们被要求填写表格时，谨慎的细节在旁观者的眼中-例如，非常主观。拥有系统记录和日志交互是至关重要的，因为系统记录的是客观的。当不是由人来记录和/或汇总并按时间顺序显示时，拥有一个系统的记录系统是非常谨慎的。

### 确定差异/偏差的能力

对于软件工程师来说，管理差异是工作的一部分。一段时间以来，源代码管理(SCM)解决方案一直表现出不同。尽管当在生产过程中遍历多个系统和配置时，潜在地，这些配置中的一些将位于与源代码分离的存储库中，或者根本不在源代码管理中表示。能够看到您的连续交付管道中发生了什么变化提供了一个很好的审计跟踪。这些差异可用作确定是否发生漂移的证据。

## 审计跟踪的用例

根据您的组织以及您面临的企业风险和法规遵从性的程度，审计跟踪可能是强制性的。虽然即使不符合法规，它们也是有益的。

### 审计/合规

这是审计追踪最典型的用例。法规和合规词汤，如受制于 SOC 2，受制于 PCI/HIPAA(机密性、健康信息、隐私、数据安全等。)法规遵从性、SOX(年度财务审计)，甚至是 FedRAMP，准确记录变更的能力对于法规遵从性环境和组织来说是非常谨慎的。

### 发布和预发布

典型的 IT 问题:谁做出了突破性的改变？系统地重放决策的能力有助于查明具体的变化。在现代无可指责的组织文化中，学习这一点很重要——并防止未来的失败。现代的趋势是在死前就开始计划；类似于死后，但在变化推出之前。大型软件部署的游戏日计划考虑到了这一点。利用以前发生的事情的审计线索可以很好地预示接下来会发生什么。

### 一般共享

由 Damon Edwards 和 John Willis 发明的 CAMS 模型是一种衡量 DevOps 成熟度的机制。CAMS 代表文化、自动化、测量和共享。看看 DevOps 的一份最新报告，其中将 CAMS 作为衡量标准，即使是精英表演组织也面临着分享的挑战。共享侧重于可见性、透明度和知识转移。

## 审计跟踪的例子

审计跟踪有多种形式。在技术领域之外，可以是财务/总账、会计分录或会计交易，甚至是餐馆或杂货店的收据。其他审计跟踪，如股票交易信息，可用于重建交易以确保合规性。当处理纯审计级别的日志信息时，寻找谨慎的信息(大海捞针)可能是一个问题，因为数据可能太宽泛/没有适当的完整性。利用 Harness，显示审计跟踪信息是一流的。

## 利用中的审计跟踪快照

使用 Harness 平台的一个好处是[审计跟踪](https://docs.harness.io/article/kihlcbcnll-audit-trail)作为一个特性内置到平台中。默认情况下，Harness 平台执行的大多数操作都可以生成审计线索。Harness 提供了一个方便的仪表板来查看审计跟踪项目。

一个简单的方法就是做出改变。例如，在这个示例应用程序中，我们决定将 Kubernetes 资源请求的内存从 300m 增加到 301m。

我们可以通过转至“安全性”->“审计跟踪”并查看最后一项来快速浏览审计跟踪日志。这些项目还记录进行更改的人的 IP 地址。

借助现成的差异(Diff)工具，您可以轻松地比较发生了哪些变化。

单击比较工具:

就这么简单，您正在实现管道中的审计跟踪覆盖。

## 持续交付的下一步

拥有审计跟踪不仅对帐户交易很重要，而且对支持 it 组织的内部控制也很重要。就连续交付而言，审计追踪的主要目的之一是捕捉修改/漂移。提供一系列的活动通常是为了团队中的成员，无论是现在还是将来。如果您想在 CI/CD 渠道中启用审计跟踪，只需[立即注册利用](https://harness.io/platform/continuous-delivery/)。

干杯，

拉维