# 什么是 CI/CD？:你需要知道的一切|线束

> 原文：<https://www.harness.io/blog/what-is-ci-cd>

这篇博文将分享你需要知道的关于 CI/CD 的一切，从代码变更到持续集成、持续交付、部署和 CI/CD 管道。

代码不存在于筒仓中。我们的软件服务应该是有价值的、被理解的和共享的。因此，软件交付的业务就是向用户和消费者发布我们的软件。[持续](https://harness.io/blog/what-is-continuous-integration/) [集成](https://harness.io/blog/what-is-continuous-integration/)和[持续交付](https://harness.io/blog/what-is-continuous-delivery/) (CI/CD)为组织提供了向用户一致交付各种软件变更的能力。这篇博文将分享你需要知道的关于 CI/CD 的一切，从代码变更到持续集成、持续交付、部署和 CI/CD 管道。

## **什么是 CI/CD？**

CI/CD 是持续集成和持续交付的简称。CI/CD 是原则、实践和能力的组合，允许各种类型的软件变更，以快速、可重复和安全的方式获得用户。这允许软件开发人员不断地集成他们的功能或服务变化，并允许 IT 和运营团队交付业务所需的标准、安全性和信心。

### **什么是持续集成？**

CI/CD 的一个主要先决条件是持续集成(CI)。CI 是一个持续集成软件开发变更的自动化过程。CI 流程自动化了源代码的构建、测试和验证。通过使用 CI 功能，开发人员可以加速他们的代码发布周期，从而减少陷入长特性开发周期和随之而来的挑战(如合并冲突)的可能性。

CI 需要一个版本控制系统来跟踪软件代码的变更和版本。Git 是一个流行的版本控制系统。使用 git 工作流，您可以启动 CI 流程。在代码库上工作的开发人员使用他们的版本控制系统将他们的更改推送到代码库中。在代码基础上工作的开发人员将这些变更合并到主代码分支中。

CI 的目标是生产一个打包的工件，准备部署到服务器或机器上。工件的一个例子可以是容器映像、WAR/JAR 文件或者任何其他可执行的打包代码。CI 自动化了从代码提交到打包工件的过程。

通常，开发人员会将一些代码提交给 Git 这样的版本控制系统，这将触发 CI 流程。通常使用静态代码分析工具来扫描或分析这个代码库，以确定代码质量。如果源代码通过了所有检查，包括单元测试，CI 流程将尝试打包或编译代码。CI 还可以包括标记或注释特定版本的代码，或者管理资源，例如版本控制系统中的分支。

实现 CI 可能是在您的团队中产生高质量代码的第一步。有许多持续集成工具可用，如 CircleCI、Travis CI、Harness CI 等等。请阅读我们关于[持续集成工具](https://harness.io/blog/continuous-integration-tools/)的文章，了解从开源工具到托管 saas 平台的更多信息。

### **什么是连续交货？**

连续交付的目标是将打包的工件交付到生产环境中。CD 自动化了整个交付过程，包括部署过程。CD 的职责可以包括提供基础设施、管理变更(标签)、部署工件、验证和监控这些变更，以及确保在出现任何问题时不会发生这些变更。

一些组织将利用连续交付的特定方面来帮助他们管理他们的操作责任。一个很好的例子是使用 CD 管道来处理基础设施的供应。一些组织将使用他们的 CD 管道，通过 Ansible、chef 或 puppet 等配置管理自动化工具来编排基础设施的配置和设置。

在连续部署中，变更是自动部署的，假设代码变更通过了 CI/CD 管道包含的所有测试和检查。与连续部署不同，在连续交付中，组织控制部署何时发生。

### **CI 和 CD 有什么区别？**

一个关于 CI 和 CD 的常见问题，它们的区别是什么？

持续集成(CI)支持软件开发团队和工作流。许多开发团队面临的最大挑战是特性开发。许多组织面临着快速交付创新和高质量产品的压力。使用代码包括开发、合并冲突、代码管理和测试，导致长的部署交付周期、不频繁的部署和高的变更失败率。解决方案是利用 CI 以自动化的方式集成开发变更，从而改进特性开发的节奏和过程。

连续交付(CD)支持运营团队和工作流。目标是安全并重复地将工件交付到生产环境中。CD 流程有助于自动化运营服务，并涉及应用程序的发布、部署和监控。当我们将一个工件提升到生产或者更高的环境中时，我们增加了验证过程的严格性。向您的测试流程和环境的每个阶段或工作流中添加额外的测试，可以让我们在客户发现这些问题之前捕捉到这些问题。

## **CI 和 CD 如何协同工作**

今天，我们将责任和目标转移到左边，以确保在软件交付过程的早期发现问题。CI 和 CD 协同工作，确保我们有能力和可见性来捕捉和修复缺陷以及潜在的生产故障或事故，否则这些故障或事故会对业务造成损害。CI/CD 管道充当自动化交付管道，模拟整个软件开发生命周期(SDLC ),否则很难理解、改进、共享和控制。

## **CI/CD 管道示例**

下面是一个基本 CI/CD 管道的图示。请注意获得一个想法或改变到生产环境所涉及的不同阶段。

您的管道可能看起来不同。没有适合所有用例的管道。不同的团队和服务有多个管道是很常见的。如果您对构建自己的 CI/CD 渠道感兴趣，我们将在 [CI/CD 最佳实践](https://harness.io/blog/ci-cd-best-practices/)指南中进一步讨论。

## **CI/CD 管道特性**

CI/CD 管道的几个特征有助于几个 [DevOps 指标](https://harness.io/blog/dora-metrics/)和洞察，值得捕捉和利用来制定数据驱动的软件交付改进和决策。这些特征与速度、可靠性和准确性相关。因此，我们关注部署频率、部署准备时间、变更失败率和平均恢复时间等指标。

为了实现这些管道特性，CI/CD 管道的典型元素将包括涉及以下内容的工具或流程:

这些元素在我们的 [CI/CD 管道](https://harness.io/blog/ci-cd-pipeline/)指南中有更详细的描述。

## **简化 CI/CD 渠道的优势**

用于创建 CI/CD 管道的优化工作流为组织和跨职能软件交付团队提供了许多好处。那么，CI/CD 有什么好处呢？以下是我们通过调查报告和与 CI/CD 平台用户的讨论发现的一些情况:

*   提高开发人员的工作效率，
*   增加代码和团队改进的时间和资源，
*   改进贡献者的反馈、协作和质量能力，
*   测试人员发现的软件缺陷和错误更少，
*   对测试的重大改进包括持续测试和自动化集成测试，
*   多个云环境的自动化 CD 管道变更，
*   使用 Kubernetes 和无服务器架构快速轻松地实现 CI/CD 管道，
*   风险更小、资源更少的更频繁的代码部署，
*   新代码和应用程序可以在不到一天的时间内加载到 CI/CD 管道中，
*   提高交付用户所需产品的能力。

## **CI/CD 工具&平台**

有许多实现 CI/CD 功能的相关解决方案。Jenkins、Spinnaker、Argo CD、GitLab、GitHub Actions 和 Harness 是一些 CI/CD 工具和平台，它们有助于为您的软件应用程序和服务创建 CI/CD 管道。如果您想查看这些解决方案的功能对比，请查看我们的 [DevOps 工具对比](https://harness.io/learn/developer/devops-tools/)。

## 利用工具按需构建、测试、部署和验证

每一个拥有软件服务的组织都与向其用户交付所述服务有利害关系。CI/CD 是组织和团队的一个核心改进领域，这些组织和团队希望提供的服务不会因为试图重现问题和重复一次性部署而带来麻烦和疲惫。这篇博文分享了你需要知道的关于 CI/CD 和软件交付的一切。如果你想了解更多，请随意[尝试利用](https://app.harness.io/auth/#/signup)，一个一体化软件交付平台。

如果你刚刚开始你的 CI/CD 工具决策，请查看我们的 [CI/CD 购买者指南](https://harness.io/learn/ebooks/buyers-guide-for-ci-cd-ebook/) -它将帮助你做出决定。