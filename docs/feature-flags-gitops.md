# 宣布:线束功能标志的 GitOps 线束

> 原文：<https://www.harness.io/blog/feature-flags-gitops>

特性标志的原生 GitOps 在这里！阅读所有关于它的内容——以及它将如何让你的生活变得更轻松。

# 宣布:线束特征标志的 GitOps

我们很高兴宣布线束特征标志的 GitOps 工作流程。更喜欢以编程方式工作的特性标志用户现在可以选择完全在开发人员工作流中管理他们的[特性标志管道](https://harness.io/blog/feature-flags-pipelines/),而无需接触 UI。

## 太多的工具，太多的用户界面，太多不同的工作方式

开发人员面临的最大挑战之一是处理工作流程中数量庞大的工具。更糟糕的是，有多种工具可以解决特定的问题，因此从一个角色到另一个角色，可能会有一组完全不同的工具。然而，所有这些的共同点是在代码中工作。

事实证明，问题不在于开发人员工具箱中的工具数量，而在于如何使用它们的大量差异，尤其是所有不同的 ui。事实是，虽然 UI 对于简化管理很重要，但是也可以在 UI 中完成的日常工作通常也可以在代码中轻松完成，如果不是更容易的话。这是每个开发人员的公共工作空间，多次使用代码只会使它更容易。

为了处理这个问题，开发团队高度要求的特性是能够在他们自己的工作流中工作(在代码中)，然后让这些变化及其影响在工具的 UI 中得到反映。开发人员希望在 UI 工作和修改代码之间做出选择。

如果我们考虑一下这是如何应用于特性标记系统的，那么很明显，标记既可以在 UI 中管理，也可以在代码中管理。虽然 UI 可以提供按照向导创建、编辑和管理标志的能力，但是创建、更改和管理标志目标的相同操作可以在代码中完成。

“Harness”管道支持发布或部署工作流，可以构建该工作流来实施标准流程或模板化部署。你可以在这篇文章中了解更多关于特征标志管道[的信息。类似于能够管理线束特性标志(标志)中最基本的工作单元，管道也可以在 UI 中处理。但是，就像管理标志一样，我们能让使用“部署语言”变得简单，让开发人员使用像 YAML 这样的声明性语言吗？](https://harness.io/blog/feature-flags-pipelines/)

## 为特性标志输入 GitOps:代码内发布管理

这个问题的解决方案和你想的差不多。除了在 UI 中构建、更新和跟踪管道之外，我们希望为用户创建使用 YAML 的能力，将这些更改提交给 Git，然后让它自动反映在 Harness UI 中。

这并不是一个新颖的概念——我们已经允许用户建立可视化管道并在 YAML 工作多年了。这个概念是 Harness 平台的核心，现在它已经成为了 Harness 特性标志。

## 它是如何工作的

即使对于那些在 UI 中工作的人来说，Harness 也会在后端为部署或发布创建相关的 YAML 文件。这意味着无论是使用 UI，还是开发人员从头开始创建 YAML 文件，Harness 都可以使用它。无论它是在哪里创建或更新的，Harness 都会自动保持它们同步——你猜对了，在 Git 中。

最终，这意味着 Harness 将始终在 Git 的最新版本上工作——我们提到过这是一个几乎即时的同步吗？一个开发人员可以提交一个新的 YAML 文件到 Git 中，然后几秒钟后就可以利用并看到他们发布工作流的更新。用户还可以选择在 Harness UI 中编辑 YAML 文件，仅在 UI 中就提供了两种处理管道的方式。

当然，除了管理发布管道之外，这也适用于管理和更改代码中的标志状态。并且这些代码内的更改都不会绕过预设的规则或治理；它们都将通过您定义的[标志管道](https://www.harness.io/blog/flag-pipelines-to-automate-feature-flag-governance-and-daily-management)进行验证。

# 如何开始

如果你想了解更多或遵循详细步骤，你可以在文档中获得更多信息[。](https://docs.harness.io/article/6f5eylg819-manage-featureflags-in-git-repos)

在产品的顶部，你会看到设置 Git 同步的选项。一旦您按照向导连接了这两个存储库，您将看到哪个存储库被连接，以及它是否被设置为同步和自动提交。这些设置将定义是否允许 GitOps 流，以及是否自动允许同步。

如果你已经在使用功能标志管道，你可以直接进入产品，你会看到一个标有“管道”的菜单项。在屏幕的顶部，你会看到一个“视觉”或“YAML”的选项，你会想要选择 YAML。当然，除非您想首先可视化地构建您的管道！

如果你还没有注册使用 Harness 但是想开始使用，你可以很容易地[永久免费注册](https://app.harness.io/auth/#/signup/?module=cf)或者[请求一个演示](https://harness.io/demo/feature-flag)。快乐发展！