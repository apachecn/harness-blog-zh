# DevSecOps 最佳实践|线束

> 原文：<https://www.harness.io/blog/best-practices-devsecops>

DevSecOps:一种方法，其中工程团队在整个 SDLC 中运行安全扫描，以在漏洞提供给最终用户之前找到并修复漏洞。让我们学习一些 DevSecOps 最佳实践。

软件开发团队面临着保持高速度的挑战，同时还要确保他们最大限度地减少产品服务中的软件漏洞。

## **为什么 DevSecOps 很重要？**

传统的应用程序安全方法很难跟上软件交付的快速步伐，因此公司已经开始使用实现 DevOps 概念的安全实践。使用这种方法，开发团队可以实现高速度的软件交付，并融入开发人员第一的安全性和治理。

DevSecOps 框架可以带来很好的结果，但是和大多数 IT 规程一样，有一些陷阱需要避免。理解和实现 DevSecOps 最佳实践是避免这些陷阱的关键。

## **devo PS 安全简介**

### **什么是 DevSecOps 方法论？**

DevSecOps 是在[软件交付生命周期(SDLC)](https://harness.io/blog/devops/software-development-life-cycle/) 的所有阶段中增加安全自动化的理念和实践。大多数 IT 专业人员都熟悉 DevOps 框架无限循环图。我们可以将循环的各个阶段映射到它们的实际实现中:

您可能认为 DevOps 安全性(也称为左移安全性)只是测试阶段的一部分，但是 DevSecOps 最佳实践是一项共同的责任，应该分布在所有阶段以确保最佳结果。

DevSecOps 的核心是一种方法，工程团队在整个软件交付生命周期中运行安全扫描，以在漏洞交付给最终用户之前找到并修复漏洞。让我们回顾一下 DevOps 安全最佳实践。

## 【DevSecOps 安全性的最佳实践

### 增强开发人员和安全人员之间的协作

正如 DevOps 哲学提倡打破工程和操作团队之间的壁垒一样，DevSecOps 原则提倡打破工程和安全团队之间的壁垒。

### 促进安全测试文化

与 DevOps 一样，DevSecOps 需要文化转变才能成功。有两种方法可以改变企业文化:

1.  自上而下的强制性变革——通常情况下，执行人员会在整个组织内传达所需的变革。
2.  自下而上的有机变化–跨团队安全协作从小规模开始，随着成功消息的传播，扩展到其他团队。

这两种方法都不容易实现，但都可以有效地创建一种文化，专注于在安全问题到达最终用户之前识别和解决它们。每个组织都需要确定哪种方法最适合他们，许多组织寻求实现两种策略的综合。

### 自动化所有安全扫描

DevOps 团队采用了一种方法，将与 CI/CD 管道相关的一切都自动化。同样的原则也适用于使用 DevSecOps 实践创建安全的应用程序。仔细检查安全应用程序交付工作流中的所有步骤有助于确定哪些可以自动化。然后，您可以根据重要性和需要付出的努力创建一个优先列表。沿着列表往下做，直到所有有意义的事情都被自动化。

### 实施自动化安全扫描器治理

治理是当今所有企业的一个重要话题。监管机构要求的法规遵从性计划要求企业跟踪并记录他们的安全措施。使用正确的工具，组织可以将策略作为代码来实施([开放策略代理](https://harness.io/blog/continuous-delivery/policy-enforced-pipeline-opa/)就是一个例子),以实施和记录经批准的软件安全扫描器的使用。这有利于标准化扫描工具的使用，同时也使其更快、更容易地通过合规性审核。

### 将安全护栏添加到开发流程中

仅仅要求和强制使用标准化的软件安全扫描工具是不够的。提供安全门或护栏也很重要，这些安全门或护栏由扫描仪的输出提供信息。同样，策略作为代码可用于使用实时扫描工具输出来控制 CI/CD 管道的工作流。

### 将 DevSecOps 视为大数据问题

DevOps 运动导致了新工具的激增，这产生了大量的数据。以类似的方式，DevSecOps 运动需要更多具有大量数据输出的工具。工具输出的分析对于通过减少生产应用程序安全漏洞来最小化业务风险是至关重要的。大数据技术，如标准化、重复数据删除、压缩、关联等。应该用于快速有效地分析扫描仪结果的组合集。

### 减少工程团队的工作量

DevSecOps 的定义可以简单到“左移应用程序安全性”虽然这过于简单，但它确实强调了一个事实，即 DevSecOps 将更多的工作量转移给了工程团队——更具体地说，转移给了开发人员。记住这一点，采用 DevSecOps 实践不要让工程团队超负荷工作是非常必要的。

我们已经讨论了在 CI/CD 管道中添加多个安全扫描器的“大数据”结果。如果不提供足够的工具，开发人员将不得不手动执行数据分析，以确定应该修复哪些漏洞、修复的优先级，并执行所有相关的工作流(创建吉拉票证、跟踪异常等)。如果不减轻工程团队的负担，DevSecOps 的实施将会变得更加困难。自然，下一个问题是“我们如何减轻我们工程团队的负担？”答案是，通过使用工具和工作流程的正确组合。查看我们的 [DevSecOps 清单](https://harness.io/learn/ebooks/devsecops-tool-checklist')以获得选择正确工具的指导。

### 自动化票据创建和跟踪

每个检测到的漏洞都应该有一个关联的吉拉票证。为了提高工程和 IT 安全团队的效率，应该自动创建这些票证。即使在检测到的漏洞是误报的情况下，您仍然需要一个票据来进行审计。正确的工具将为您创建这些吉拉票证，并将它们与检测到漏洞的应用程序服务相关联。漏洞得到补救(修复得到验证)后，票证应该会自动更新和关闭。

### 根据需要更新您的工具

到目前为止，几乎所有讨论的最佳实践都需要工具来协助自动化或分析。传统的 IT 安全工具在设计时没有考虑到现代开发运维实践和云原生技术。公司应该重新评估所需的工具，以确保他们的 DevSecOps 计划成功。

许多组织都在纠结是构建还是购买的决策。对于大多数公司来说，为不断变化的环境构建复杂的工具通常是不切实际的。因此，当您评估适合您组织需求的工具时，您可能会发现我们的 DevSecOps 清单是一个有用的参考。

### 投资工作流程

检测到新漏洞时会发生什么？申请和跟踪安全豁免的流程是什么？如何通知其他团队安全豁免？其中一些流程和工作流可能已经存在于您的组织中，但有些可能需要创建。无论是现有的还是新创建的，这些工作流都需要自动化，以便在您的组织中扩展安全实践。

### 考虑应用程序的整个生命周期

如果您已经采用了 DevSecOps，那么您应该明白，仅仅在工件进入生产阶段之后运行安全扫描是不够的。安全扫描必须在应用程序服务的整个生命周期中实施。

*   **CI 管道**
*   *软件组合分析(SCA)*——识别用于构建应用服务的开源软件或第三方组件中的[漏洞](https://harness.io/blog/devops/vulnerability-scanning-ci-cd-pipeline/)。
    SCA 工具的例子:黑鸭 SCA， [Snyk](https://harness.io/blog/continuous-delivery/snyk-harness-vulnerabilities/) ，白源 SCA。
*   *静态应用程序安全测试(SAST)*——对应用程序的源代码或字节码执行静态代码分析。
    SAST 工具的例子:Brakeman，SonarQube，ShiftLeft。
*   **CD 管道和生产作业**
*   *基础架构即代码(IaC)测试* -基础架构安全性的子集，软件定义的计算、网络和存储的漏洞评估。
    IaC 测试工具的例子:Checkov，TFLint，Terrafirma。
*   *动态应用程序安全测试(DAST)* -在运行时分析应用程序，以确定是否存在漏洞。
    DAST 工具的例子:MicroFocus Fortify、OWASP ZAP、HCL AppScan。
*   *交互式应用安全测试(IAST)*——结合 SAST 和 DAST 的元素，通常在 JVM 或 CLR 中。
    IAST 工具的例子:Checkmarx IAST，HCL AppScan Enterprise，Synopsys Seeker。
*   *容器安全测试* -应用容器和 Kubernetes 配置的安全分析。
    集装箱测试工具示例:Qualys、Docker Bench for Security、Aqua Container Security。
*   *模糊测试*——故意将不良信息输入到正在运行的应用程序中，以确定安全漏洞状态。
    Fuzz 测试工具的例子:Beyond Security beSTORM，Synopsys Fuzzing Test Suite，Google OSS-Fuzz。
*   *API 测试*——对 API 端点进行专门测试，以识别安全问题。
    API 测试工具的例子:Apigee，Katalon Studio，Astra。

## **结论:通过更新安全工具和流程来跟上变化的速度**

DevSecOps 不仅仅是让开发人员运行安全测试。它是关于以开发人员第一的心态实现安全自动化，将信息安全扩展到安全专家小组之外，并降低最终用户面临的安全风险。最大的挑战是在不降低软件交付速度的情况下完成所有这些。

随着当今应用程序中使用的云原生技术和开源组件的激增，安全工具和流程必须更新以跟上变化的速度。传统的安全工具和流程不适合现代环境。

利用[安全测试编排](https://harness.io/products/security-testing-orchestration) (STO)可以帮助您实现本文中讨论的最佳实践。STO 在软件交付生命周期中无缝集成安全扫描，提供策略即代码治理，并执行使您的 DevSecOps 项目成功所需的大数据分析。您准备好采用 DevSecOps 实践了吗？[下载我们的清单](https://harness.io/learn/ebooks/devsecops-tool-checklist)，其中列出了您想要涵盖的关键能力。