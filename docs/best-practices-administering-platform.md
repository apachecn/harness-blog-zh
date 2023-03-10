# 管理 Harness 软件交付平台| Harness 的最佳实践

> 原文：<https://www.harness.io/blog/best-practices-administering-platform>

用户、用户组和资源——天哪！了解一些管理 Harness 平台的最佳实践。

这个博客提供了如何在 Harness 平台中最好地组织用户、用户组和资源的指导，以有效地组织您的团队，实现有效协作的目标，同时最小化组织开销。根据您可能拥有的组织结构类型，我们的建议基于您希望实现的一些关键目标。这个博客并不提供明确的说明，而是一组建议的样本，应该对其进行修改以适应您的组织的需求。

## 结构很重要

一个组织的结构可以让人们更容易一起工作，更快地移动。或者，它会使人们更难合作并获得想要的结果。应用程序和平台也是如此——应用程序或平台(在这种情况下，我们将互换使用“平台”和“应用程序”)提供的设置和组织用户的功能可以帮助组织提高效率，也可以通过增加复杂性和管理开销来降低效率。应用程序应该允许客户以符合组织理念的方式进行设置，并反映人们如何一起工作的指导原则。

对于 Harness 在我们客户的软件交付生命周期中扮演的关键角色来说，让我们的客户高效是很重要的。同时，我们必须让他们容易管理平台。我们认识到，无论组织结构如何，它们都可能专注于以下一个或多个目标:

1.  增强协作
2.  提高响应能力
3.  最小化成本
4.  避免重复
5.  保持监督
6.  实现合规性

因为没有一个放之四海而皆准的标准，而且不同的组织都是以最有助于他们实现目标的方式建立的，所以 Harness 提供了一个灵活的模型，可以用来创建满足您需求的结构。在本帖中，我们将研究组织设置 Harness 的各种方法。此外，我们还将回顾有助于他们提高效率的最佳实践。

## 积木

线束平台中有四个主要构建模块。这些可以用来以最有助于你实现目标的方式进行设置。

**层次元素** : Harness 提供了一个层次结构来组织用户、资源和项目。

1.  **项目**:在最底层，有一些项目可以用来将在一个项目中作为一个团队工作的用户组织在一起。项目独立存在所需的所有相应资源也可以在项目中创建，或者可以从父项目继承。
2.  **组织**:一个组织代表一个逻辑实体，用于将多个项目组织在一起。这有助于创建职责分离和资源隔离。组织是表示多条总线或产品线的有效方式。组织也是在不影响现有实体的情况下建立新收购企业的有效方式。
3.  **账户**:账户是线束中的顶层实体或根节点。在帐户级别创建的用户要么用于管理管理功能，要么用于监督所有组织和项目。在帐户层创建的资源可以在所有组织和项目中使用。

**资源组**:资源组是对需要作为一个单元一起管理的资源进行分组的一种非常有效的方式。资源组可以包含所有类型的所有资源，或者特定类型的所有资源(例如，所有秘密管理器)或者命名资源(例如，秘密管理器 X1 和云提供商 Y1)。这为资源分组和权限控制提供了极大的灵活性，便于管理和建立明确的职责分离。

用户组:用户组是一种简单的方法，可以将从事相同项目并具有相似角色的用户组合在一起。用户组是为具有类似职责的用户管理权限和通知首选项的便捷方式。

**角色**:角色是一组允许或拒绝对资源执行操作的权限。当角色被分配给用户或用户组，然后应用于资源组时，它允许用户对资源组中的一组资源执行角色中定义的操作。

下图显示了如何将用户分组到一起以形成用户组的概念视图，这些用户组又被赋予应用于不同范围的资源组的角色。

## 推荐

使用上述构建模块，客户可以创建一个适合他们需求的结构，从创建一个完全开放和扁平的结构，到一个具有明确边界的完全粒状的结构，以及介于两者之间的一切。让我们来看看影响如何构建线束决策的一些关键因素，以及相应的建议。我们将使用以下因素作为关键决策标准来建议最佳结构。

1.  组织的规模
2.  组织结构的类型
3.  集中的
4.  分散的
5.  业务单位/产品线的数量
6.  组织希望实现的关键目标

下面是一些代表性的结构和基于组织想要实现的关键目标的相应建议。

### 设置 1:只有一条产品线的小型组织

基于这样一个假设，即这样一个组织想要实现的关键目标是高度协作和责任共担，Harness 建议如下:

**设置**:单组织多项目。

**资源**:所有资源都是在账户级别创建的，只有非常有限的资源是在项目级别创建的。

**用户/用户组**:所有的用户和用户组都是在账户级别创建的，根据他们的角色提供跨所有项目的权限。

### 设置 2:拥有多个产品线的中型组织

随着规模的增长，重点转移到有效管理资源上，同时继续关注协作和速度。如果重点是集中管理资源，同时分散执行，那么 Harness 建议如下:

**设置**:每个产品线或 BU 一个组织。

**资源**:所有资源都是在帐户级别创建的，只有非常特定的资源是在组织或项目级别创建的**。**

**用户/用户组**:管理员用户(或需要管理资源的用户)在帐户级别创建。需要维护监督或实施治理的用户在整个帐户或组织内被授予适当的权限。其余的用户只被授予他们需要处理的项目的权限。

### 设置 3:拥有多个业务单位的大型组织

大型组织通常有多个业务部门，每个业务部门负责自己的损益。这要求他们单独管理自己的资源。有时，业务的性质也阻止了资源跨总线共享。如果重点是在分散执行的同时分散管理资源，那么 Harness 建议如下:

**设置**:每个产品线或 BU 以及每个新收购的实体一个组织。

**资源**:资源不是在账户级别创建的。组织中跨项目的公共资源在组织级别创建，其余资源在项目级别创建**。**

**用户/用户组**:管理员用户在账户级别创建。需要维护监督或实施治理的用户在整个帐户或组织内被授予适当的权限。其余的用户只被授予他们需要处理的项目的权限。

## 摘要

根据您的组织是如何设置的以及您想要实现的关键目标，您可以使用不同的选项来设置 Harness 软件交付平台。这些选项将帮助您以有效和高效的方式获得想要的结果。

你愿意继续阅读技术文章吗？我们在这里为你准备了一些:[服务账户:CI/CD 自动化之路](https://harness.io/blog/service-accounts-cicd-automation/)和[使用 Redis 流的事件驱动架构](https://harness.io/blog/event-driven-architecture-redis-streams/)。如果你错过了我关于 Harness 软件交付平台中的[用户&角色管理的第一篇文章，今天就去读吧！](https://harness.io/blog/user-role-management/)

-卡皮尔