# BigQuery 浪费了令人震惊的 1.5 万美元的云开支|利用

> 原文：<https://www.harness.io/blog/bigquery-wasted-cloud-spend>

账单不再令人震惊:学习一些 BigQuery 最佳实践，再也不用担心月底的云账单。

想象一下，一觉醒来，你的云账单出现了惊人的峰值，你的 Google BigQuery 成本也出现了巨大的峰值，你不得不四处寻找问题的根源。这是不可取的，但也并不罕见。我们需要首先对事件做出反应，并主动实施方法来避免将来出现此类高峰。在这篇博客中，我们将探讨识别成本峰值的方法，一些需要设置的防护栏，以及控制 BigQuery 成本的 3 个最佳实践。

## 挖掘 BigQuery

Google BigQuery 有一个定价模型，用户根据扫描的数据量付费。我们很容易忽略这些成本，因为传统上，我们只为数据库的计算能力付费，理论上，我们可以运行大量的查询。客观地看，价值 1.5 万美元的支出相当于扫描 3000 TB 的数据。这相当于 10 名开发人员运行 10 个查询，扫描大约 30 TB 的数据。当我们这样说的时候，它看起来不是很不现实，不是吗？

确定成本峰值可能具有挑战性，但这一点至关重要，因为如果我们不这样做，当我们在月底查看我们的云账单时，它可能会滚雪球般变成一项巨大的负债。一种方法是在 GCP 为每个独特的项目和服务组合建立[预算和警报](https://cloud.google.com/billing/docs/how-to/budgets#add-new-budget)，但是一旦我们有大量的项目，这就变得很难管理。我们内部不需要管理该用例的 GCP 预算，因为[云成本管理](https://harness.io/products/cloud-cost/)的异常检测功能使用机器学习检测任何意外的成本峰值，通知流入 slack。

Anomaly Detection Inside Harness Cloud Cost Management

Anomaly Detection Slack Notifications

我们可以做些什么来设置护栏，以避免将来出现这样的成本高峰？我们可以为 [BigQuery](https://cloud.google.com/bigquery/docs/custom-quotas) 设置定制的成本控制。设置项目级和用户级配额有助于设置每天重置的使用上限。这可以限制特定用户运行太多昂贵的查询，也可以从整体上限制特定项目超出预算。为了避免引发大量查询，我们还可以限制单个查询的最大计费字节数。

但有时，这可能不是最佳解决方案。当我们知道我们对 BigQuery 的分析将会很广泛时，guardrails 可能会偶尔妨碍生产力。在这种情况下，我们可以选择提交到 [BigQuery Slots](https://cloud.google.com/bigquery/docs/slots) 来享受统一价格。此外，如果我们确实知道使用行为本质上是有峰值的(例如:我们一天只运行 1 小时的分析工作)，我们可以考虑购买 [BigQuery Flex Slots](https://cloud.google.com/blog/products/data-analytics/introducing-bigquery-flex-slots) 而不是整个月的承诺，GCP 提供了预留低至 60 秒的计算能力的灵活性。仅在高峰使用期间保留灵活插槽可以避免长期承诺和供应商锁定，同时优化成本。

## BigQuery 的 3 个云成本最佳实践

### 减少扫描的数据量

*   使用群集和分区来减少扫描的数据量。
*   聚类和分区有助于减少查询处理的数据量。若要限制查询聚集表或分区表时扫描的分区数量，请使用谓词过滤器。
*   对聚集表运行查询时，在聚集列上添加筛选器可以减少扫描的数据。
*   当查询已分区表时，分区列上的筛选器用于修剪分区，因此可以降低查询成本。
*   不要运行查询来浏览或预览表数据。
*   如果试验或探索数据，用户可以使用表预览选项免费查看数据，而不会影响配额。
*   仅查询您需要的列。
*   只包括分析所需的列。SELECT *是 BigQuery 中开销最大的查询方式。

### BigQuery 中的存储成本

90 天(长期存储)或以上未编辑的表中的数据比活动存储便宜 50%。为了利用这一点，请确保不要编辑表格。因此，最佳实践是将新数据移动到新的分区中，这使得表的分区变得很重要。

在数据集、表和分区级别有各种到期选项。我们通常会创建表并忘记清理它们，因此建议在创建时设置表和分区的到期时间，以避免成本堆积。

如果我们有使用云函数或 GCP 数据流的无服务器 ETL 管道设置，我们可能有中间暂存表，这可能并不总是给最终用户增加很多价值。因此，我们应该清理这样的中间表，以避免存储开销。

### 智能缓存和流成本

只有当数据必须立即可用时，我们才应该使用流插入。背后的原因非常简单:*流式插入*到 BigQuery 是收费的，通过*批量插入*加载数据是免费的。

BigQuery 将结果缓存在一个临时的缓存结果表中。缓存是为每个用户和每个项目维护的。因此，运行重复查询将从缓存中获取结果，并且不会对这些结果计费。此外，如果多个微服务是相同/相似的查询，跨微服务使用相同的服务帐户有助于利用缓存，因为缓存是针对每个用户的。

## 结论

在 Harness，我们使用我们的[云成本管理](https://harness.io/products/cloud-cost/)商业智能仪表盘来深入了解每个查询、每个用户级别的 BigQuery 成本，并找出排名靠前的查询，进一步优化它们以降低成本。要了解更多关于云成本管理的信息，请立即申请一个[演示](https://harness.io/demo/)。