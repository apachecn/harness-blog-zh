# 我们的旅程远离詹金斯，走向驾驭 CI | Harness

> 原文：<https://www.harness.io/blog/away-from-jenkins-harness-ci>

Harness 和许多其他公司一样，使用 Jenkins 作为我们软件交付过程的 CI 部分。我们有超过 300 个任务，平均每天生成大约 4，000 个构建。

本文是与 Srinivas Bandi、Dinesh Garg 和 Shivakumar Ningappa 合作撰写的。

Harness 和许多其他公司一样，使用 Jenkins 作为我们软件交付过程的 CI 部分。我们有超过 300 个任务，平均每天生成大约 4，000 个构建。

随着时间的推移，我们受到了其他 Jenkins 用户面临的常见[痛点和难题](https://harness.io/blog/continuous-delivery/dependency-plugin-hell-jenkins/)的影响:

*   Jenkins 主管理和资源问题:构建团队花费了大量时间来解决主管理问题。Jenkins 节点上也有许多 CPU 和内存峰值。
*   中断:构建团队每周都会经历中断，这影响了开发人员的工作效率和带宽。
*   可用性:Jenkins 没有提供“单一窗格”管道视图，导航到旧版本也很麻烦。缺少现成的仪表板也是一个严重的缺点。
*   非容器原生:Jenkins 已经有二十多年的历史了，主要是为物理构建机器设计的，对容器和 K8s 的支持是后来才想到的。

## 构建现代 CI 解决方案

Harness 构建自己的 CI 解决方案的主要动机是创建一个现代化的工具来改进开发人员的构建和测试时间。Harness 已经意识到，目前市场上的工具，如 Jenkins，非常差，已经过时。Jenkins 没有提供基于 Docker 的架构、云和 SCM 不可知论、图形视图、流水线步骤的能力、SaaS 选项——还需要我多说吗？考虑到痛点(如上所列)和挑战，以及对[开发人员体验](//harness.io/ebook-one-developer-experience/)的关注，Harness 着手创建一个更好的 CI 解决方案。最终结果是我们的最新产品:线束 CI。

我们很高兴在我们自己的应用程序上测试 Harness CI，看看它对于企业级软件应用程序有多成功。有了 327 个詹金斯职位，我们知道迁移将是大规模的。首先，我们进行了差距分析，以确定和解决 CI 中的一些关键功能差距。我们在 Junit 报告集成、问题注释触发器支持和重新触发时中止中发现了差距。我们很快就建立了这些能力。

## 我们的詹金斯迁移战略

通过差距分析，我们还确定了哪些工作需要迁移，以便树立信心并证明我们产品的成功。我们决定专注于我们的主要后端回购。这个存储库是我们 Jenkins 管道中最复杂的，使用了所有 Jenkins 功能的 90%。缩小我们的关注范围，我们能够将我们的迁移工作减少到大约 25 个工作，并且知道如果我们成功地迁移了这些工作，剩下的工作将非常简单。

在这个存储库中，我们从发布构建管道开始。这个管道用于生成发布工件，然后部署到 QA 进行测试，最后发布到生产。由于它们对控制操作至关重要，我们确保为 Jenkins 准备了备份。我们用这个管道开始了迁移，因为它很关键，但也因为它是由 QE 团队以受控的方式运行的。如果我们发现了 Harness CI 的任何问题，我们可以在 Jenkins 上触发相同的管道来生成构建。作为迁移过程的一部分，我们分析了作业，并将其分解为小的功能组件。对于每个组件，我们都制定了最佳的方式来实现相同的线束 CI。例如，在 Jenkins 中，我们使用管道链来运行并行隔离步骤，而在 Harness CI 中，我们使用并行步骤来实现同样的功能，这使我们能够更好地查看和控制管道执行。

接下来，我们决定移动“公关检查管道”这一功能至关重要，因为 PR 检查是合并到 master 中的所有代码的主干，因此影响到 Harness 中 100 多名后端工程师中的每一个人。我们决定采取分阶段的方法。两周以来，我们以影子模式运行这些检查，以建立信心并解决任何问题。一旦我们确认一切正常，在这两个星期过去后，我们将剩余的管道转移到 CI。

在整个迁移过程中，我们发现并解决了许多问题，包括一些性能瓶颈、导致构建停滞的竞争条件以及 pod 清理问题。这个练习帮助我们建立了基础，并为贬低詹金斯铺平了道路。

在我们迁移了主要的后端回购之后，我们没有遇到任何重大意外。我们为 6 月的第一周设定了完整的迁移截止日期，每个团队都努力在不到 3 周的时间内淘汰剩余的 300 多个职位。

## 后 Jenkins 迁移结果

### 100k+基于线束配置项

在过去的几个月里，我们成功运行了 Harness CI。Harness CI 已经支持了超过 100，000 个构建，包括 1000 多个发布和功能构建以及 90，000 多个 PR 检查。

### 减少开发人员的挫折感

跨团队 1:1 中最常见的抱怨之一是 Jenkins 的不可靠性。当我们最初开始扩展我们的工程团队时，我们遇到了几次中断，这全面影响了开发人员的生产力。

有了 Harness CI，开发人员的挫折感大大降低，因为上面列出的痛点都解决了。后端工程师 Abhinav Singh 分享了他的想法:“运行 Jenkins 正在成为一场噩梦，因为我们无法扩展它，而且它经常出现故障。即使查看它的线程转储并找出根本原因也非常困难，因为它只有几个 GB。等待事情得到解决，我不得不浪费很多时间，这造成了很大的挫折。从我们开始利用 CI 开始，大多数问题都得到了解决，我们几乎没有停机和扩展问题。此外，让 Jenkins 加入任何新的开发人员，这就像查看日志文件一样是一项艰巨的任务。在 Jenkins 周围导航不是很直观，入职时必须有人扶着开发人员。让新开发人员掌握 CI 很容易，只需几个小时。”

### 提高构建团队的生产力

构建团队的相当大一部分带宽被分配用于维护 Jenkins。随着 Jenkins 的离开，他们现在可以将时间集中在解决开发人员的生产力问题上。

## Jenkins 或任何其他 CI 产品从未有过的新功能

测试智能(TI)是利用 CI 的独特功能。我们的 CI 模块附带了针对 Java 单元测试的智能测试选择和执行功能。我们的测试智能算法根据代码变化智能地识别要执行的测试，从而大大减少测试周期时间。为了客观地看待这一点，请查看下面我们直接从 TI 环境中提取的指标。

### 测试智能节省时间

为了进一步测试我们的测试智能功能，我们针对开源项目运行了它，以查看构建过程的速度有多快。数据如下所示。

Cost savings of Harness Continuous Integration Test Intelligence with common open-source projects

通过查看这些数据，我们很高兴地看到使用测试智能节省了时间，并进一步展示了我们 CI 模块的与众不同的特性。

我们目前看到，由于测试智能，基础设施成本节省了 25%。(关于这一点的详细信息以及其他发现即将发布！)

## 结论

对 Harness 来说，迁移到 Harness CI 是一个巨大的胜利。我们能够从 Jenkins 迁移出来，并在我们自己创建的持续集成工具上成功运行，了解市场上当前解决方案的痛点。我们不建议每个人都开始构建自己的 CI 解决方案。做好这件事很难，我们已经为你做了所有的艰苦工作。相反，您可以尝试今天为自己驾驭 CI。采取第一步来结束开发人员的挫败感，并请求一个 [Harness CI](https://harness.io/platform/continuous-integration/) 的演示。