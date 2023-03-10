# 云日志优化-我们如何节省超过 14 万美元的日志成本|利用

> 原文：<https://www.harness.io/blog/cloud-logging-optimization>

了解我们如何节省超过 14 万美元的云日志成本。通过利用多种实践，我们能够识别昂贵的日志。

在公共云世界中，没有什么是免费的。[日志记录](https://harness.io/blog/modern-log-layers/)有时被认为是事后的想法，但却是能够审计和洞察系统的重要部分。随着向公共云的迁移，如果不加检查，日志会变得昂贵；原因可能是我们已经习惯了自己系统上一定程度的日志保留和冗长，并期望在公共云中也是如此。

在 Harness，我们使用谷歌云平台(GCP)来托管我们的生产环境，我们非常积极地优化我们的云使用和管理云账单。随着我们的服务规模不断扩大，我们最近注意到，我们在伐木上的支出已经成为 GCP 总账单的重要组成部分。在我们采取行动之前，伐木每天花费我们大约 800 美元。

### 了解我们的伐木成本

对于公共云服务，您的最终成本通常是跨越多个服务维度(如存储和数据传输)的[总和。在 GCP，云日志](https://harness.io/blog/cloud-billing/)[的价格](https://cloud.google.com/stackdriver/pricing#logging-costs)是基于使用量的，每摄取一 GiB 的日志需要 0.50 美元。我们开始调查日志量的主要来源。日志接收仪表板指出 Google Kubernetes 引擎(GKE)容器和 Global(我们的代表接收)是日志量的两大来源。第三个是云 HTTP 负载平衡器。

这是有意义的，因为大多数利用工作负载是在 GKE 集群，这是第一类。全局类别是我们从代表那里接收的日志，也就是在客户环境中运行的 Harness 组件。

为了进一步分析，我们希望了解集群中的哪些工作负载是该成本的主要来源。对于这种聚合功能，我们将[日志接收器](https://cloud.google.com/logging/docs/export)配置为[大查询](https://cloud.google.com/logging/docs/export/bigquery)。一旦我们在 BigQuery 中有了几天的日志数据，我们就能够运行丰富的查询，并进一步将日志数据分解成其来源。

为了进一步深入这些表中的日志，我们必须了解代码中的哪些组件对日志有贡献/写入。我们为每个[日志条目](https://cloud.google.com/logging/docs/reference/v2/rest/v2/LogEntry)将日志数据组织成一个 JSON 有效负载。这使我们能够对日志进行丰富的查询。在这些有效负载中，我们放置了关于源代码类、源节点的信息，以及特定于客户帐户的信息。利用这一点，我们能够快速地将成本归因于噪声最大的不同代码区域。

有了成本数据，我们就能够开始围绕优化制定战略。

### 优化我们的伐木成本

我们采取了一些措施来优化云日志支出。以下是最有用的:

1.  **配置日志排除**。我们不知道这个[宝石的一个特点](https://cloud.google.com/logging/docs/exclusions)云日志。有了这个，我们已经不再摄入大部分的噪音了。

2.  **为我们出于审计目的需要保留的日志配置 GCS/BigQuery** 的日志接收器，但这样我们就不必在云日志中为它们付费。

3.  **减少特别是**噪音部件**中的日志**。一些源代码产生了不成比例的高日志量。虽然对于较低的规模来说这不是问题，但这并没有用，事实上，随着服务的增长，这削弱了我们有效调试的能力。我们跟踪了个别开发人员，删除了不必要的日志行。

这一努力的直接结果是显而易见的。几天之内，我们已经将日志记录方面的云支出减少了一半，相当于每年节省超过 140，000 美元。

希望我们的经验能帮助您优化自己的云日志支出。其他公共云供应商也可以采取类似的方法。节约成本是我们[云成本管理](https://harness.io/platform/cloud-cost-management/)产品的一个目标，我们每天都在践行这些价值观。如果您还没有看到云成本管理的实际应用，请立即[请求演示](https://harness.io/platform/cloud-cost-management/)。