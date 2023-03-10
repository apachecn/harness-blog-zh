# 部署 3 倍多的软件，停机风险降低 75 %|

> 原文：<https://www.harness.io/blog/deploy-more-software-with-less-downtime>

多部署，少破坏。这成为了 Entur 的现实。

## 关于 Entur

Entur 被赋予了一项伟大的任务，那就是让挪威的公共交通选择一条可持续发展的道路变得简单。要做到这一点，有必要为运输部门创造新的统一解决方案。为了实现创新，我们通过开放 API 收集、增强和共享公共交通的公共数据。

## **不可信的部署**

Entur 使用 CircleCI 进行持续集成和软件交付。该公司对他们的 CI 流程很满意，但达到了定制脚本 CircleCI 管道的限制。这些管道是用 1000 条 xml 线配置的，这使得维护和更新它们成为一场噩梦。

每个 CircleCI 管道都是用 1000 行 xml 配置的。

> Tommy A. Bø | DevOps 工程师| Entur

Entur 组建了一个世界级的部署团队来解决 CircleCI 的缺点:

*   Tommy A. Bø，DevOps 工程师
*   云架构师 Recep Cetin
*   Tor Magnus Castberg，组长

该团队需要简化软件交付，并让开发人员对部署管道充满信心。部署每两周进行一次，变更失败率为 20%。每次生产部署失败都需要 2 小时的手动回滚。开发人员担心部署管道的稳定性，无意中造成了重大的中断。更糟糕的是，部署管道的维护占用了开发人员增强核心业务功能的宝贵时间。

我们不需要一种工具来管理自己，这样我们就可以专注于我们的核心业务。

> Tommy A. Bø | DevOps 工程师| Entur

## **开箱速度和安全性**

Entur 选择 Harness 来满足他们的连续交付需求，以简化复杂的 CD 过程，消除管理另一个工具的负担，并为开发人员提供自助式连续交付。

我们选择 Harness 是为了引人注目的用户界面和直观的工作流程

> Tommy A. Bø | DevOps 工程师| Entur

Harness 让 Entur 的开发人员能够自行部署，而不用担心会弄坏东西。Entur 的部署速度增加到每周两次，并且利用持续验证帮助将变更失败率降低到 5%。即使出现故障，Entur 也可以在 5 分钟内通过点击按钮回滚。

所有这些都不需要维护数千行 xml 配置。

Harness 简单易用，在跨平台部署时，它减少了我的人工工作量。

> Recep Cetin |云架构师| Entur