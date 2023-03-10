# 如何处理云成本管理中的闲置资源

> 原文：<https://www.harness.io/blog/idle-resources>

闲置资源可能会让您的组织在云计算成本上损失数千美元。了解如何使用 Harness 处理闲置资源。

闲置资源是账单冲击的主要原因，并且与未分配的资源一起，是云成本优化世界中容易实现的结果。在过去的几个月里，我们已经发布了一些关于如何缩减或[合理调整资源](https://harness.io/blog/cloud-cost-management/reduce-cloud-costs/)以及如何[管理 Kubernetes 成本](https://harness.io/blog/cloud-cost-management/kubernetes-cost-analysis/)的精彩博客帖子——以及其他云成本管理策略——但我们从未详细讨论过闲置资源。现在是时候了！

## 什么是闲置资源？

首先，资源基本上是你在云中可用的 CPU 和内存——你的计算资源。在云资源的世界中，这些资源通常分为三类:已利用的、空闲的和未分配的。很明显，被利用的资源就是今天正在使用的资源。未分配的资源是根本没有使用的资源，或者是没有分配给实例的资源——非常不经济。闲置资源是在某个时间点使用过，但现在没有使用的资源；资源的闲置也定义为资源没有被完全利用(例如，您只使用了 m4.xlarge EC2 实例的 20%,导致 80%的闲置)。通常，闲置和未分配的资源来自过度配置的资源，可以缩减或调整大小。对于开发人员来说，很难限制他们认为创建高性能应用程序所需的资源数量…所以我们认为引用赫特人贾巴的话是合适的:“没有讨价还价的余地，年轻的绝地武士…”但是*可以*节省成本。

我们在 Kubernetes 的[成本管理策略](https://harness.io/ebook-cost-management-kubernetes/)电子书中深入探讨了大量关于闲置和未分配资源的细节，该书虽然专门针对 Kubernetes，但确实有许多信息可以应用于三大云提供商(亚马逊网络服务(AWS)、谷歌云平台(GCP)和微软 Azure)的通用资源。

就像我们说的:低垂的果实。虽然纠正不适当的资源分配很容易，但我们不要低估闲置资源对云成本的影响。不幸的是，这些资源会导致数千美元的绝对浪费，因此对它们进行控制非常重要！35%的云支出是浪费，因此要密切关注资源。将需要一些长期规划，但是使用云成本管理工具是一个很好的起点。这些工具是一种很好的帮助方式——特别是像[云自动停止](https://harness.io/blog/product-updates/cloud-autostopping/)这样的功能，可以在不再需要资源时停止它们，并在必要时自动重新打开它们，以及异常检测，它使用机器学习来识别奇怪的成本峰值并提醒你问题。像这样的见解非常具有可操作性。

## 闲置资源对云成本有什么影响？

在分配资源时，开发人员并不总是知道将要使用多少资源。当他们为其构建环境建立基础设施时，会对将要消耗和需要的 CPU 和内存量的资源限制进行粗略估计。通常这些资源会被过度分配，并且很难估计出所需资源的正确数量。但这对于降低云成本至关重要。拥有比所需更多的资源是在浪费金钱，因为这可能会导致您的云账单飙升！

为了描述实际发生的情况，假设公司 A 正在使用 AWS，并且已经提供了 EC2 大型实例，但是意识到它们只使用了 40%的资源。公司可以实例化中型实例，比如说每单位节省 5 美元，而不是提供数千个每单位花费 10 美元的大型实例。当然，公司 A 需要时间来了解中型实例是否能够满足其基本和过剩的容量需求，但问题是，如果 60%的现有大型实例未被使用，向下移动一个层将有助于显著降低闲置利用率并提高效率。

## 闲置资源的主要来源

自从第一批经济体诞生以来，全世界的资本家都在努力降低商业成本。这种做法的经济学意义在于创造更大的现金余额，这意味着公司的潜在价值更大。

由于与云资源相关，降低这些成本是下一个前沿领域的一部分。闲置资源的理论很简单:工程师想要高性能的应用程序，因此在过度配置方面犯了错误，导致了闲置的云成本。

但是最大的罪犯是什么呢？当然，我们谈论的是计算资源。

### 按需实例/虚拟机

有些人可能称之为终极闲置资源。按需提供的资源很容易升级和扩展，同样也很容易被遗忘。这可能会导致资源在根本没有使用的情况下花费金钱，或者导致资源的大小不合适，并且永远不会得到正确的大小。

为了解决这些问题，我们可以调整大小，以便有最小的空闲容量，或者我们可以在不使用这些资源时关闭它们，这样就不太需要为用例找到绝对正确的实例。

## Harness 如何处理空闲资源

在 Harness，我们将闲置的云资源视为工程团队日常工作的副产品。因为工程师被激励快速创新并优先考虑高性能应用程序，他们被给予自由支配来旋转必要的云资源。很多时候，这意味着他们将做出判断，导致过度调配资源，从而确保性能永远不会成为最终用户的问题。

然而，许多组织内的经济环境不利于持续维持闲置资源的高开销。这不符合成本效益，而且从长期来看，这么做所需的那部分资本是不可持续的。由于过多的闲置资源开销，即使云提供商提供最优惠的折扣，组织最终也会为其云支付过高的费用。

同时，很难将这种开销保持在最低水平，因为在部署应用程序更改后，很少会考虑调配的云资源所有者的决策。如果有一种自动减少开销的方法会怎么样？我想到了两种方法:自动调整资源大小或取消资源供应；或者，保留现有资源，但在不使用时将其关闭。

### 解决闲置云资源问题

引入利用云成本管理。你可以把它想象成智能云成本管理。该产品模块的一个关键功能是云自动停止，它允许用户以两种方式解决问题:

1.  不使用时自动关闭计算资源-削减高达 75%的成本。
2.  为资源动态编排 spot 实例—相同的基础架构，价格低 70-90%。

对于前一种功能，用户可以注册现有的计算资源组，之后该工具将最大限度地减少这些资源的空闲时间。用户可以定义一个“关闭周期”，当没有任何流量到达资源的阈值时，Harness 将关闭它。但这不仅仅是关闭它们——当检测到资源的流量时，它还会再次打开它们。

而对于后者，很简单。用户只需要求系统将注册的计算资源组作为 spot 实例运行，Harness 会处理剩下的工作！Harness 将处理 spot 实例的编排，并保证没有 spot 中断。通过这种方式，用户不必太担心成本，因为任何给定实例的成本都会降低 70-90%。

## 结论

闲置的云资源是云成本管理世界的唾手可得的果实，但它们不一定是一件麻烦的事情。虽然用户完全可以自己分析闲置资源，并找到调整大小的方法，但为什么不跳过艰苦的工作，通过在不使用时不付费来简单地优化呢？

利用智能和自动化来管理云成本，并立即消除与管理闲置云成本相关的麻烦。今天就报名参加[演示](https://harness.io/platform/cloud-cost-management/)！