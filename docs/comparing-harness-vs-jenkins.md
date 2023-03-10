# 比较 CI/CD 的 Harness 和 Jenkins | Harness

> 原文：<https://www.harness.io/blog/comparing-harness-vs-jenkins>

Jenkins 是一个 CI 解决方案，可以扩展到 CD。线束提供 CI 和 CD 模块。带线束的主 CI/CD。

我们在 2018 年的原始比较是应许多使用/使用 Jenkins 的客户的要求进行的，他们希望为他们的内部讨论提供一份书面材料。Harness 是这个领域的新玩家，很自然，我们会被比作最流行的工具。当时，我们专注于 CD。我们从来不拐弯抹角地说 CI 和 CD 是不同的过程，应该如此对待。Jenkins 是 CI 工具，Harness 是 CD 工具，两个产品在 2018 年的核心竞争力几乎没有重叠。

几年后，我们通过收购 Drone.io 和推出 Harness CI Enterprise 进入了 CI 领域。我们将所有业务从[詹金斯转移到我们自己的产品](https://harness.io/blog/away-from-jenkins-harness-ci/)。

这是马具大战詹金斯，2021 版！

## 启动并运行

对大多数人来说，DevOps 是达到目的的手段。把你的软件交到你的用户手中是目标。除了少数非常有经验的 Jenkins 实践者之外，假设您已经准备好了基础设施，那么您的第一次构建和运行需要花费 30 分钟到几个小时的时间。在您可以简单地运行“hello world”构建之前，有一长串插件要添加，设置要调整，最后基础设施要整合。

相比之下，在 Harness 中注册一个帐户后，不到 15 分钟就可以开始运行管道。注册，添加您的目标基础设施和工件服务器，在几分钟内开始构建和部署。在我们的文档中有一整节[致力于各种基础设施类型的快速入门，不需要插件。](https://docs.harness.io/article/u8lgzsi7b3-quickstarts)

## CI 与 CD

这是一个我们将从山顶呼喊直到时间结束的声音。这些年来，很多被称为 CD 的东西都是上面堆着脚本的 CI 工具。到目前为止，詹金斯是这一类中的佼佼者。虽然插件和解决方案是在事后添加的，以减少对脚本的需求，但它本质上仍然是一个 CI 工具。对于常见/常规用例，Jenkins *实际上可以*实现 CD。然而，这一切最终都落在了您的 DevOps 员工身上，他们站出来维护您的 Jenkins 基础架构，更新插件，并在出现问题时进行故障排除。

Harness CD 是专门为解决向各种基础设施交付软件时遇到的特定挑战而构建的，同时保持了高水平的可配置性。Harness 在 CD 的各个方面都有 150 多个集成，从连接到您的基础设施到集成变更管理。最终，它通过结合 APM/日志记录工具来主动检测版本问题，从而确保了一个闭环。所有这些集成都不需要我们的客户进行维护或保养。此外，安全和治理是驾驭 CD 的一等公民。在部署领域，配置不当的访问或缺乏可审核性可能会导致罚款，甚至更糟，成为头条新闻。

两个段落很难做到这一点公正，所以我会给你指出以下四篇文章更多。可以说，Harness 让一个又一个客户升级了他们的 CD 游戏。

[持续集成(CI) &持续交付(CD)有什么区别？](https://harness.io/blog/continuous-integration-continuous-delivery/)

[什么是 CI/CD？你需要知道的一切](https://harness.io/blog/what-is-ci-cd/)

[你不做连续交货的 10 个征兆](https://harness.io/blog/10-signs-you-dont-do-continuous-delivery/)

[持续交付与持续部署:有什么区别？](https://harness.io/blog/continuous-delivery-vs-continuous-deployment/)

## 维护

谈到 Jenkins，我们从客户那里听到的最常见的问题之一就是维护。不管他们的设置工作得多好，很少有人认为它是可持续和可扩展的，因为维护它需要时间和精力。这些挑战包括维护和更新底层基础设施、插件、各种脚本、安全更新等。这还是在他们应对这些变化带来的下游影响之前。

最终，Jenkins 本身变成了一个内部软件产品，必须进行维护、版本控制和测试。维护工作是一个挑战，但找到做这项工作的人又增加了一层。软件正在接管世界，就业市场的扩张速度超过了开发人员的数量。在维护这样的问题上投入更多的人是一个无法扩展的解决方案。此外，每个致力于交付的开发人员并没有致力于取悦你的客户。

相比之下，Harness CI/CD 对于维护来说是轻量级的(这是我们的客户 [Luma](https://harness.io/customers/case-studies/luma-ditches-jenkins-for-harness/) 、 [intelliflo](https://harness.io/customers/case-studies/increasing-deployment-velocity/) 、 [BetterCloud](https://harness.io/customers/case-studies/drop-jenkins-deploy-faster/) -好吧，我停下来，你明白了)，允许自助服务，同时保持强大的防护，并避免了插件蔓延的陷阱，从开发人员开销、安全性到性能影响。用于线束的基础设施占地面积也相当小，需要最少的维护。

## 连续累计

曾几何时，仅仅是集中脚本和协调工作人员就已经改变了游戏规则。然后，声明性管道出现了，并进行了调整。然后是容器化的建造。然后测试优化。

大多数软件解决方案都是从一个地方开始，随着时间的推移而发展，对每个人来说都是一样的，因此有膨胀和脆弱的趋势。

现代 CI 方法的候选名单包括:

*   声明管道
*   集装箱化步骤
*   测试优化
*   AI/ML 以提高效率
*   安全性
*   与源代码控制紧密集成

Harness 的 CI 解决方案是根据现代软件开发的需求从头开始构建的。我们从基于容器的构建系统开始，以避免依赖性并增加可扩展性。之后，我们添加了使用机器学习的测试优化，以减少测试周期。此外，我们为管道开发实现了托管 Git 体验。最后，我们将一切都包装在企业级安全和治理中，如机密管理、审计跟踪和 RBAC。听起来很有趣？或许很神奇？阅读[驾驭 CI 企业](https://harness.io/blog/introducing-harness-ci-enterprise/)的详细内容。

## 灵活性

说句公道话，詹金斯非常灵活。每样东西都有一个插件，每种用例都有不同的脚本编写方式，并且有许多不同的配置可供部署。对于扩展这种方法有一些合理的担忧，但是有了合适的 DevOps 工程师和良好的设计，这是可行的——并且*已经为许多组织工作过了。*

Harness 集成了现成的几个不同的构造，允许针对独特的用例进行定制。在 Harness CD 中，模板库、shell 步骤和定制部署类型使得几乎任何用例都成为可能。Harness CIE 提供了一个基于容器的插件系统，以一种轻量级的方式来实现你可以想象的任何用例。

## 摘要

Jenkins 是一个非常有用的工具，它可以做很多事情。我们在 Harness 用了很长时间是有原因的。但最终，随着规模的扩大，你会开始看到在 Jenkins 上构建任何东西的方法的局限性，包括维护、辛劳和停机。

当我们讨论 Jenkins 时，我们最想强调的是投资回报和总拥有成本。如果你是一家只有少量服务的小公司，Jenkins 可以带来巨大的投资回报。当你开始扩大用例、服务、开发人员等等的规模时，你每小时投资的回报往往会以指数速度下降。

最后，在做所有的计算时，考虑解决方案的实际成本。前面提到了一些案例，在这些案例中，我们的客户从 Jenkins 这样的“免费”解决方案中节省了大量资金。当你考虑基础设施和开发者的所有成本时，“免费”这个词绝对应该加引号。

下一步是什么？您可以在[从 Jenkins 迁移到驾驭 CIE:旅程](https://harness.io/blog/jenkins-to-cie-journey/)中了解更多关于我们的技术之旅，以及我们为什么认为 CI 需要一种全新的方法……当然，您可以亲自动手[亲自尝试这项技术](https://app.harness.io/auth/#/signup/?module=ci)！