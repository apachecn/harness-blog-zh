# 利用 OPA | Harness 平衡开发人员自由和治理

> 原文：<https://www.harness.io/blog/balancing-developer-freedom-and-governance-with-opa>

除了好啤酒，开发人员快乐的下一个最大组成部分是获得工具和过程来快速有效地完成他们的工作。

在企业软件中，没有比“开发人员体验”更时髦的词汇了在过去十年中，随着组织转向 DevOps 模式以提高速度和实现更大的业务灵活性，从以运营为中心的心态到以开发为中心的方法的演变令人惊叹。向以开发者为中心的方法的转变也推动了对云和平台工程的大量投资。

改善企业中的开发人员体验是一项非常具有挑战性的任务。从历史上来看，在大多数企业环境中，一个新的开发人员通常需要 6 个多月的时间来了解在企业环境中开始真正高效工作所需的工具、系统和过程。

## 什么让一个开发者开心？

除了好啤酒，开发人员快乐的下一个最大组成部分是获得工具和过程来快速有效地完成他们的工作。历史上，在大多数企业中，开发人员不得不使用糟糕的遗留工具。他们受限于缓慢的内部基础设施，并试图将变更审查过程复杂化，这会将生产发布减缓到年度或季度事件。

有一种新的开发人员，他们只知道即时访问基础设施和管道自动化的云原生世界，不再接受过去开发人员无法控制交付自动化的范式。这些“出生在云端的开发者”正是企业努力吸引和努力留住的。

那么，为什么不给开发者他们想要的任何东西而不附加任何条件呢？

## 平台工程的困境

构建软件交付服务的平台工程团队想要的无非是给开发人员打开王国的钥匙，然后离开他们的方式。挑战是在加强安全性、治理和可用性的同时给予团队控制权。历史上，平台工程团队很难给开发者自由。Harness 在 2017 年引入了具有增强治理控制的 CD 即服务，帮助解决了部分问题。然而，即使有了细粒度的基于角色的访问控制和模板，在大多数受监管的环境中，任何涉及生产的管道阶段都受到严格控制。那么，当谈到软件交付的共享服务时，成熟度有多高呢？这个博客将强调交付成熟度的不同阶段以及每个阶段的特征。

## 软件交付成熟度阶段

### 第一阶段:对所有人免费

除了在初创公司的早期阶段，这种成熟度很少出现，但是当持续集成(CI)首次被采用时，这种成熟度非常普遍。每个开发团队都有自己的软件交付工具，几乎没有标准化或治理。如果其他团队参与到交付过程中，那么工件被扔过墙，并且几乎没有关于如何有效地运行或排除故障的文档，这是很常见的。

### 第二阶段:封锁

在第一阶段的车间发生一些事情之后，通常是重大的生产事故，下一个成熟度级别是软件交付的完全锁定。这是平台工程团队接管过程的地方，但是面向业务的团队对过程几乎没有控制。任何管道变更都涉及到平台工程以及漫长的等待时间。事实上，无人机创始人 Brad Ryzenski 创建 CI 工具的动机之一是，他工作的银行需要等待数月才能将库更改为静态 Jenkins runners。今天，这种类型的软件交付场景在许多受监管的组织中仍然非常普遍。

### 第三阶段:脚踝手镯

对于拥有平台工程团队的大型企业来说，这可能是最常见的软件交付场景，这些团队已经采用了专门构建的连续交付(CD)收费。他们有权允许开发人员修改管道以满足他们的需求，但任何涉及生产级环境的管道或管道阶段都受到严格监管。开发人员可以修改较低的环境阶段，但只有少数人可以修改生产管道。这导致了业务单元和平台工程之间的许多摩擦，并且通常减慢了发布速度。

### 阶段 4:策略驱动的自助服务

这是平台工程团队在软件交付中所能达到的最高成熟度。在这个成熟度级别，生产路径由基于策略的治理方法驱动，该方法定义了生产发布的需求。安全扫描、功能测试、变更管理批准以及生产版本的任何其他要求都被定义为策略即代码。使用软件交付服务的业务单元对他们的交付管道拥有完全的控制权，并且治理的实施由他们的策略作为代码集中管理。

## 借助 OPA 实现真正的开发人员自助服务

那么，如果实现真正的开发人员自助服务只需要采用策略即代码，为什么平台工程团队没有广泛采用这种方法呢？有很多事情会阻碍组织将策略作为代码来采用。在开放策略代理(OPA)作为策略代码的标准出现之前，在软件交付中实现策略代码并不容易。另一个阻碍策略驱动的自助服务的因素是，大多数组织中的 CD 仍然是 CI 工具，在大多数组织中编排脚本。拥有 CD 的声明性方法是策略驱动软件交付的一个要求。

OPA 是一种强大的声明式方法，它将策略定义为代码，并将安全策略与应用程序版本分离，从而实现真正的基于策略的大规模治理。Harness 是第一个拥有以 OPA 为中心的治理方法的软件交付平台。在 Harness 之前，pipelines 集成基于策略的检查的唯一方式是使用插件或源代码库挂钩，这通常会导致用户体验脱节并抑制采用。

在 Harness 平台中，OPA 策略是一等公民，有助于在我们的整个平台上实施治理。策略创作是本机构建的，并且在管道的保存和运行上实施策略的能力使组织能够从一开始就防止创建不兼容的管道。

策略即代码超越了跨越 Harness 平台其他功能的管道。管道外 OPA 实施的一个很好的例子是[利用特性标志](https://harness.io/products/feature-flags)。大多数企业刚刚开始采用共享服务方法来采用特征标志，跨不同业务单位管理标准可能非常具有挑战性。通过 OPA 策略和利用特性标志，共享服务团队可以实施标志命名标准和要求。

我们看到采用的最受欢迎的策略之一是能够防止在生产中启用在特定较低环境中未启用的标志。已经有许多未经测试的特性切换导致停机(或者，在 Knight Capital Group 的情况下，导致破产)的广为人知的例子，因此基于策略的治理对于任何采用特性管理的组织来说都是必须的。

## 使用 OPA 解放您的开发人员

这是一个以开发人员为中心的世界，坚实的平台工程基础是保持开发人员和产品所有者对高发布速度满意的一个优势。软件交付的最终成熟度是一种基于策略的治理方法，它让开发人员可以自由地修改他们自己的生产路径。Harness 是业内唯一一个通过采用 OPA 作为本机功能，对基于策略的治理采取整体方法的软件交付平台。

要了解更多信息，[请观看我们的 Harness OPA 功能演示](https://harness.io/company/contact-sales)。