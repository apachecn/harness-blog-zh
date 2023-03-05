# GitOps 架构说明|线束

> 原文：<https://www.harness.io/blog/gitops-architecture-explained>

在本文中，我们将讨论使 GitOps 成为可能的底层架构，以及您需要的工具和入门建议。

采用[gitop 最佳实践](https://harness.io/blog/devops/what-is-gitops/)意味着使用 Git 作为单一的事实来源来管理您的软件开发过程和自动化基础设施。当您部署应用程序时，您的连续交付(CD)工具会自动部署、回滚或前滚必要的集群来支持它。您的 GitOps 实践越先进，实际上自动发生的就越多。GitOps 将基础架构管理和自动化的精华与 DevOps 最佳实践相结合，以实现持续部署。

在其最终形式中，GitOps 意味着不再需要人工基础设施工作，这意味着更快的发布速度。这意味着进行蓝/绿和金丝雀部署，使用机器学习来检测故障，并在必要时完全自行回滚部署，包括集群。

但是需要什么来支持它，从哪里开始呢？在本文中，我们将讨论使 GitOps 成为可能的底层架构，以及您需要的工具和入门建议。

那么，[GitOps 是如何工作的](https://harness.io/blog/gitops)？GitOps 原则是现代持续部署不可或缺的一部分。 [GitOps](https://harness.io/blog/devops/what-is-gitops/) 是一种面向公司的方法，旨在简化云原生应用的部署，并让开发人员在如何交付应用方面拥有更多自主权。无论是添加防火墙规则、定义 VPC，还是修复 UI 错误，所有这些都应该来自源代码控制的中心层面。

GitOps 关注的是“是什么”,而不是“如何”,其中所有应用程序组件都是以声明方式编写的描述，而不是关于如何完成构建它们的指导。在声明性范例中，开发人员用代码描述他们期望的状态，并且他们与之交互的系统以满足所描述的需求的方式确定何时、如何以及在何处放置应用程序，并且自动将该期望的状态与集群的实际状态相匹配。

声明式基础设施和声明式配置的主要好处是，它们允许软件开发团队首先关注他们的应用程序，而不是部署和运行时的逻辑。换句话说，GitOps 使开发人员能够使用基础设施自动化，或者将[基础设施作为代码](https://harness.io/blog/infrastructure-as-code)，在整个部署过程中减少摩擦或批准瓶颈。

查看我们针对云基础设施的[gitop 最佳实践](https://harness.io/blog/gitops-best-practices)指南。

## GitOps 和持续部署有什么关系？

要在基础设施管理中实践实施 GitOps 工作流，您需要五样东西:

1.  源代码控制系统
2.  持续集成(CI)工具
3.  像 Docker 这样的容器化工具
4.  像 Kubernetes 这样的容器编排工具
5.  像 Argo CD 或 Flux 这样的容器代理/控制器]

让我们来详细探讨每一个。

### 1.像 Git 这样的版本控制系统

当您将基础设施定义为代码时，您将把它存储在 Git 存储库中。那会成为你真理的来源。您的 CD 代理将监视并将其与实际集群配置进行比较。这些配置文件将存储为代码，以便每次部署相同的基础设施环境。

### 2.持续集成(CI)工具

通过 CI 工具运行 pull 请求允许您使用配置文件将测试合并到声明定义的 GitOps 基础设施部署中。这是基础设施管理的一个关键部分:自动化测试，以便您可以在提交之前修复 bug，这对您的 GitOps 工作流至关重要。

### 3.像 Docker 这样的容器化工具

为了让 GitOps 工作，在软件开发期间，您需要对您的微服务使用容器化来打包您的代码、依赖项、配置、流程等等。

### 4.像 Kubernetes 这样的容器编排工具

您将需要像 Kubernetes 这样的工具来协调您的容器部署。当您为您的 CD 工具安装代理时，您将把它安装在您的 Kubernetes 集群上。

### 5.像 Argo CD 或 Flux 这样的容器代理/控制器

像 Argo CD 这样的控制器是 GitOps 发挥作用的原因。您将在 Kubernetes 集群上安装它的代理，它将监视源代码控制系统中 Git 定义的基础设施和实际生产环境之间的差异，并使它们保持同步。

总的来说，这些工具提供了在 Git 中定义基础设施所需的大部分内容，并且当人们向应用程序提交代码时，这些工具可以自动实现基础设施。让我们来详细探讨其中的每一个步骤。

## 实施 GitOps 架构

### 首先，将您的 GitOps 架构容器化

不言而喻，但是第一步是使用像 Docker 这样的容器工具来容器化应用程序。通常使用和这样的工具，使用 Kubernetes(也许还有 Terraform)以声明的方式管理基础设施，因此它以代码的形式存在，并协调变化。

### 其次，用 Git 存储库定义您的基础设施

您需要在 Git 中定义您的基础设施，这意味着您需要一种将基础设施转化为代码的方法。对许多人来说，这意味着使用 Kubernetes，因为声明性代码更容易使用，因为您可以为所有配置文件实现版本控制。这也可能意味着使用[舵图](https://helm.sh/)来管理数据包，或 [Kustomize](https://kustomize.io/) ，来更容易地管理您的配置和 YAML 模板。

在 Git 存储库中定义和存储的基础设施成为基础设施真相的唯一来源。所有其他版本或描述，包括那些当前生产中的集群，都被认为与该事实同步或不同步。

[引用:您在 Git repo 中定义和存储的基础架构成为您了解基础架构真相的唯一来源。]

在 Git 中，有几种方法可以用来存储基础设施:

**选项 1:维护一个 Git 存储库**

在这个存储库中，您将创建至少两个分支:一个用于应用程序，一个用于环境(基础设施)。这是更简单的方法，因为少了一个需要管理的存储库，并且您的应用分支可以包含您的所有微服务。唯一的缺点是它提供了对基础设施的访问，而您可能并不总是希望允许这样做。

**选项 2:维护两个或更多的 Git 存储库**

至少为您的应用程序和环境分别创建一个存储库。这使您可以更好地控制谁可以访问您的生产环境，并允许开发人员和操作团队在单独的存储库中工作，如果他们愿意的话。但是，需要管理的工作更多。

### 第三，将您期望的和实际的 GitOps 基础设施状态与版本控制系统同步

接下来，您需要配置您的 CI 工具，以便它能够自动解决您在 Git 中期望的集群状态和您的生产环境中的实际状态之间的差异。概括地说，有两种方法可以做到这一点:

‍ **1。推送配置更改**

在更传统的设置中，您可以在管道中构建一个触发器，以便它执行一个命令，将您想要的基础设施状态推入生产环境。(通常，使用 Jenkins 或 CI/CD 工具。)虽然这会将您的集群更新到新定义的状态，但问题是这是单向的、被动的。如果两个州有分歧，就没有自动执行。您的集群可能处于错误循环中，Jenkins 永远不会检测或解决它，因为这不是它的初衷。您必须自己检测错误并推送更新，这可能很烦人，因为您还必须更新应用程序。

‍ **2。拉动配置更改**

更新集群的更新、更灵活的方法是安装 Argo CD 之类的代理，以主动监控和解决 Git 中的期望状态和实际集群状态之间的差异。这样做的好处是代理不断地检查这两种状态是否同步。如果它们不同步，它就会采取行动。而且，它是双向的。如果生产环境不同步，it 可以发现并解决这个问题。

### 第四，教您的团队使用 GitOps 进行部署

基础设施团队开始在 Git 中使用拉请求和合并，以及开发人员选择他们自己的基础设施，通常需要一点文化上的改变。但总的来说，这是减少大量手动基础架构部署工作的途径。

一旦您的架构建立起来，下面是实际工作的方式:

1.  基础设施团队在 Git 存储库中预先定义声明所需的基础设施
2.  作为应用程序拉取请求的一部分，开发人员引用他们想要部署到的环境
3.  基础设施、安全或其他团队审查拉取请求
4.  拉请求被合并
5.  GitOps 代理(如 Argo CD)检测更新的容器映像，并将集群状态与最近更新的提交同步
6.  GitOps 代理确认同步已完成

## 使用 GitOps 实现高级连续交付

在开发云原生应用程序时，GitOps 可以为您节省大量时间和精力，否则这些时间和精力将花费在手工任务上。您可以在部署过程中使用 YAML 文件部署基础架构，而不是手动配置基础架构。有了合适的架构和工具，可以监控 Git 定义的实际基础设施状态并解决它们，您就消除了快速发布的一大障碍。

免费开始使用 Harness CD & GitOps as a Service！