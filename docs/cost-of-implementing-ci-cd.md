# 构建与购买-实施 CI/CD |利用的成本

> 原文：<https://www.harness.io/blog/cost-of-implementing-ci-cd>

与物理硬件相比，软件是无形的，当利用软件来满足所需目标时，大多数组织经历的一个常见练习是构建与购买分析。与物理基础设施相关的东西不同，软件唯一可感知的材料是时间和努力。

对于组织来说，价值计算与纯粹的时间和精力相比可能难以计算。即使是今天的物理硬件，在推动公共云的同时，也进行了相同数量的构建与购买分析；构建/扩展数据中心或启动云资源。

价值计算不仅要考虑时间和材料，还要考虑总拥有成本和机会成本；关键资源被占用而无法向外部客户提供核心功能给企业带来的成本。

对于大多数组织来说，建立一个 [CI/CD 平台](https://harness.io/blog/what-is-cicd-platform-why-should-i-care/)并不是组织的核心。构建大量的功能和工具来将特性功能投入生产并不能为组织增加价值。具有讽刺意味的是，“你的外部客户不关心你如何做某事”这句谚语对你的内部客户来说并不一样。CI/CD 系统直接影响您的内部客户，他们非常关心如何实现目标。CI/CD 平台可以呈现类似于外部客户/业务价值驱动应用程序的生命。想要采用 CI/CD 的组织确实有一些先决条件。

## CI/CD 平台先决条件

在 DevOps 的“人员、过程和技术”三要素中，实现持续集成和持续交付需要在所有三个支柱上的投资和文化转变。CI/CD 平台本身并不自动意味着您的组织正在实现完全的持续集成和持续交付。一个良好架构和采用的 CI/CD 平台允许在平台中利用意见，并提供护栏和来自不同团队的专家意见作为指路明灯。

最大的先决条件是理解 CI/CD 平台是一项不断发展的技术，应该被视为一种产品而不是一个项目。这些平台需要支持的技术继续发展，需要包含在 [CI/CD 管道](https://harness.io/blog/ci-cd-pipeline/)中的项目继续左移/自动化。

从技术的角度来看，对于 [CI/CD](https://harness.io/blog/what-is-ci-cd/) 的[持续集成](https://harness.io/blog/what-is-continuous-integration/)部分，某种可以向外部系统发送事件的源代码管理(SCM)解决方案以及捕获和存储构建的工件库是基础部分。对于[连续交付](https://harness.io/blog/what-is-continuous-delivery/)部分，向代码化/自动化方向发展，以支持应用程序所需的信心和基础设施。这些可能是实现自动化测试覆盖和某种基础设施自动化/规划的第一步，以便在部署时创建基础设施或准备好进行部署(例如，启动云资源或部署到等待的 Kubernetes 集群)。像任何软件事业一样，用宽画笔绘画需要受到范围的约束。

## 界定 CI/CD 要求和 MVP 的范围

以工程效率为任务的团队希望在他们构建的平台中包含尽可能多的组织。大多数企业都有异构的技术堆栈，其中的某些部分可能已经存在了几十年。构建自动化来支持 100%的企业可能需要几年时间，并且随着某些技术被弃用或被引入，这将是一场持续的战斗。这就是范围很重要的原因。

在构建平台时，一种常见的方法是尝试解决最具影响力或支持最多内部客户的项目。第一步是对组织中的技术选择进行普查。在选择技术时，规划和尽职调查非常重要。对于那些不喜欢 ITIL/ITSM 的人来说，这可能是这些流程大放异彩的一次，尤其是在较大的企业中，给出了技术选择的简明图片。在与客户或潜在客户合作时，我们在 Harness 所做的部分工作是帮助进行持续交付能力评估(CDCA ),以记录和衡量成熟度。该目录的一部分还盘点了技术选择。

在构建最低可行产品(MVP)时，需要平衡的两个因素是，客户最容易成功，还是广泛采用和影响。要实现这两个目标是很棒的，但通常情况下，你需要选择一条路。好消息是，渐进的成功会带来成功和动力，如果您开始构建更简单的功能，随着时间的推移，您会获得平台方面的专业知识。CI 和 CD 都有不同的要求。

### 持续集成需求和 MVP

持续集成的目的是构建自动化。持续集成平台有三个主要支柱:构建的可重复性、一致性和可用性。现代的方法是任何种类的源代码管理——甚至是提交/合并——都应该被期望开始一个构建。

随着持续集成成为主流，软件交付过程中一个具有讽刺意味的瓶颈开始成为 CI 系统。并发构建的数量随着工程师和新包装的数量而增加。例如创建 Docker 映像会是计算密集型的，CI 系统会很紧张，并且会有很长的队列。一个核心要求是 CI 系统应该设计成可伸缩的，以满足企业的需求。这可以是分布式构建运行器的形式，在需要或不需要时上下旋转。

从依赖的角度来看，在外部系统上构建与在本地机器上构建没有什么不同。语言和特定于包的构建工具需要分布在 CI 系统的构建运行程序中。如果在您的本地构建中有其他的关卡，比如代码质量或者单元测试需求，这些也需要分布到构建发生的所有地方。在几个构建发生之后，一个可行的发布候选被制作/需要被部署，从而过渡到连续交付。

### 连续交付要求和 MVP

当与 DevOps 的“人、过程和技术”三要素中更偏重于技术的持续集成相比时，持续交付代表了另外两点。连续交付的目标是将变更安全地部署到生产中。传统上，对安全的信心是由人的协调批准和几个不同的测试和验证过程带来的。

[部署和交付](https://harness.io/blog/continuous-delivery-vs-continuous-deployment/)是有区别的；持续部署与持续交付。部署侧重于分发/安装应用程序二进制文件的实际行为，通常采取阻力最小的方式。交付侧重于生产中的安全和信心建设。持续交付的一个标志是[金丝雀发布](https://harness.io/blog/blue-green-canary-deployment-strategies/)，这是一个增量发布。金丝雀的发布在技术上更复杂，因为它们代表了随着金丝雀迈向完全流量的几个增量发布和判断呼叫。

持续交付的挑战是建立不愉快的路径。失败是必然会发生的，如何优雅地重启、恢复或调试一个进程是一个挑战。至少，在构建自己的 CD 平台时，工作流应该是创建的第一个功能。能够系统地记录从工件到生产的所有步骤，即使其中一些步骤现在是手工的，对于识别重复的瓶颈并最终引入自动化是至关重要的。构建任何软件都需要时间、所有权、承诺和迭代。

## 构建您的 CI/CD 平台

创建和构建软件需要一个村庄。对于那些有运营背景并且仍然记得基于票证的解决方案的人来说，创建 CI/CD 平台不仅仅是一张可以采取行动的票证。

软件，尤其是你的 CI/CD 平台，有一个生命周期。如果您以前经历过软件开发生命周期(SDLC ),那么利用几个开源项目，可能结合商业工具来创建功能，将会非常熟悉。

为了获得长寿和采用，可能需要几种资源。为您的 CI/CD 平台采用产品思维需要产品级资源，从产品经理到编写、运行和执行质量任务的多种类型的工程师，再到销售解决方案所需的内部支持者。

根据公司的规模，只关注开发和质量保证资源所需的全部成本，你可以看到成本是如何快速增加的，这甚至没有考虑机会成本。

与 CI/CD 平台支持的应用程序一样，任何应用程序的大部分成本都是在最初发布之后。这可以是对不太令人兴奋的 SDLC 维护/修补阶段的持续增强。一旦获得新平台的最初高潮过去，仍然需要资源和投资来维护 CI/CD 平台。

### 维护您的 CI/CD 平台

确保平台的寿命是维护 CI/CD 平台的核心。维护 CI/CD 平台的支柱是:通过新功能确保增长以适应技术趋势，提供可扩展的基础架构，开展最佳实践培训，修补/升级/中断修复，以及管理任务，如应用程序和用户的加入/离开。

潜在的定制解决方案不仅需要专业知识，还需要所有其他各种任务和投资来进一步推动平台的采用、稳定性和效率。有经验的软件工程师可以分析出一个初始项目的样子，但是肯定有未知的东西——尤其是效率方面。

### CI/CD 的未知

技术格言是正确的:有了无限的时间和资源，你可以建造任何东西。即使您构建了最棒的平台，鼓励反模式也可能会耗费企业的资金。

如果平台太具体，并且没有包括足够的组织，它可以符合“只是多了一个工具”的类别在 CI/CD 平台上运行一个部署或加入一个新服务需要成本。

如果部署应该全天进行，团队需要做多少准备工作才能提交到 CI/CD 平台？手动测试和批准越多，CI/CD 平台的维护人员和内部客户需要的时间就越多。

诸如安全性、可靠性、可伸缩性和验证之类的非功能性需求可以活生生地吃掉任何软件平台。像任何软件一样，需要符合企业标准。随着 CI/CD 平台在企业中变得越来越重要，正常运行时间和可伸缩性需求开始变得越来越像一个面向客户的外部应用程序，它得到了开发和运营团队的全力支持。另一个超越生活的格言是，“如果你擅长某事，你就不应该免费去做。”从寻求货币化的项目到为你的组织构建和维护一般开销，免费开源肯定是有成本的。

### 开源 CI/CD 不是免费的

开源是一种研究和开发方法。在工业界，也有开源免费的假设；这意味着免费的许可费用。相反，有数百种潜在的开源软件(OSS)许可，可以考虑知识产权收费。

在 CI/CD 领域，开源项目更倾向于以引擎为中心。与开源纯粹主义者谈论项目背后的货币化策略是一个令人不安的话题。流行的 CI/CD 项目可以由销售项目背后的企业版和服务的商业组织赞助。打个汽车的比方，如果你免费得到发动机，你需要座椅、车身和一系列安全功能，比如安全气囊，来完成汽车。通常，企业需要的项目，如安全加固、特定修补，甚至支持，都归入 OSS CI/CD 项目的付费企业版。

汽车的完成、维护和升级正是使用免费开源项目的成本:沉没成本。如果需要改变，只有两个选择。一种是构建所需的功能或自己进行更改，或者去游说开源项目以了解您所需的功能，并希望有人在适当的时候构建该功能。开源项目也有不同的发布和补丁时间表；利用几个项目意味着几倍的维护。

从一家专注于 CI/CD 类工具的公司购买一个平台——并考虑到平台的所有正交关注点，具有很大的价值主张。

## 购买您的 CI/CD 平台

作为一个工程组织，购买解决方案可能会打击你的自尊心。作为一名工程师或工程负责人，很明显你有很高的技能，有能力建造需要的东西；如果我们不喜欢建造东西和解决复杂的问题，我们就不会成为工程师。购买的主要驱动因素是将功能投入生产的时间和精力是否值得在自建平台上保留大量工程资源。

在考虑购买 CI/CD 平台时，价值和关注是驱动因素。当先前已经在构建 CI/CD 平台方面进行了投资时，决策变得更加困难。如果从零开始可以逆向设计利用商业和开源解决方案所需的时间和精力。

利用 Harness 解决了双重挑战:确保平台继续包含过去、现在和未来的技术，并满足现代企业所需的所有需求，如可伸缩性和安全性。Harness 从众多客户那里学到了经验，并每天都在不断改进平台。

Harness 的使命是实现部署标准化，让每家公司都能像 FAANG(脸书、苹果、亚马逊、网飞、谷歌)组织一样复杂地部署，就像使用您最喜欢的消费应用程序一样简单。在 Harness 平台中，关于部署的大多数部落知识(什么是正常的，什么是不正常的)都被 AI/ML 解锁并民主化。

[Harness Platform](https://harness.io/products/platform/) 非常灵活，允许您的组织或团队根据需要进行或多或少的自动化。Harness 平台无处不在，您可以在其中进行部署，并坚持鼓励最佳实践和阻止反模式。Harness 是 UX CI/CD 采用方面的专家，致力于帮助企业实现更频繁、稳定和安全的部署。具有讽刺意味的是，部署有相关的成本，内部客户需要资源来处理和验证部署。与 Harness 合作的一部分是帮助您通过我们的持续交付能力评估来计算价值。

## 不做任何与 CI/CD 相关的事情的成本

在 Harness 2020 上，我们发布了一份关于组织正在经历的 CI/CD 旅程的[初步研究。这些组织处于其 CI/CD 之旅的不同阶段。在与 Harness 合作之前，Harness 帮助提供的价值工程的一部分是对当前土地进行普查。我们已经完成了数百次持续交付能力评估，2020 年，我们汇总了结果。](https://harness.io/learn/ebooks/continuous-delivery-insights-2020-ebook/)

列举了组织面临的几个挑战，部署方面仍有大量工作要做。根据我们在 2020 年对企业的调查，部署频率的中位数是 10 天。平均而言，每一次为期十天的部署都需要八个小时的准备时间，这意味着甚至开始部署都需要一整天的准备时间。飞行中的验证，然后完成部署，平均需要 25 小时的工程负担。那是一个全职员工半个多星期的工作量。

做一些数学计算，如果你想知道工程师的花费，看看[玻璃门](https://www.glassdoor.com)、[关卡](https://www.levels.fyi/)或[百叶窗](https://www.teamblind.com/)会给你一个很好的当今市场价格的指示。将构建平台的人力成本和每次部署的人力成本相加，乘以您的公司平均部署的次数，将得出将功能投入生产的实际成本。没有考虑的是不关注核心能力的机会成本，如果在部署期间出现故障，这些时间的影响可能会高得多。Harness 是用来消除软件交付中的恐慌的。

## Harness，您软件交付的合作伙伴和平台

从第一天起，我们就肩负着使软件交付民主化的使命。该平台不断扩展功能，使软件交付对每个人来说都很容易。有一个专业知识的宝库在利用，致力于使您的 CI/CD 目标-和超越-成为可能。请随时与我们联系，如果您还没有，请注册一个[线束帐户](https://app.harness.io/auth/#/signup/)。

干杯！

拉维