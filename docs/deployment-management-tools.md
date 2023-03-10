# 部署管理工具:Chef 与 Puppet 与 Ansible 与 SaltStack 与 Fabric | Harness

> 原文：<https://www.harness.io/blog/deployment-management-tools>

部署管理工具的比较，包括 Chef、Puppet、Ansible、SaltStack 和 Fabric。

如今，在生产环境中工作通常意味着持续的部署和遍布全球的环境。当您的基础架构是分散的和基于云的，并且您正在处理在基本相同的服务器上频繁部署基本相同的服务时，拥有一种自动配置和维护一切的方法是一大优势。部署管理工具和配置管理工具就是为此而设计的。它们使您能够使用配方、行动手册、模板或任何术语来简化整个环境中的自动化和流程编排，从而提供标准、一致的部署。

在这一领域选择工具时，需要考虑几个因素。一个是工具的模型。有些需要主-客户机模型，这种模型使用一个集中的控制点与分布的机器进行通信，而有些则可以或确实在更局部的级别上操作。另一个考虑因素是你所处环境的构成。有些工具是用不同的语言编写的，对特定操作系统或设置的支持可能会有所不同。确保您选择的工具能够很好地适应您的环境和您团队的特殊技能，可以为您省去很多麻烦。

## 1.Ansible

Ansible 是一款开源工具，用于将应用部署到远程节点，并以可重复的方式提供服务器。它为您提供了一个通用框架，用于使用推送模型设置来推送多层应用程序和应用程序构件，不过如果您愿意，也可以将其设置为主客户端。Ansible 建立在行动手册的基础上，您可以将这些行动手册应用于各种系统来部署您的应用程序。

**何时使用:**如果快速轻松地启动并运行对您很重要，并且您不想在远程节点或托管服务器上安装代理，请考虑 Ansible。如果您的需求或关注点更多地在系统管理员方面，这很好。Ansible 专注于精简和快速，因此如果这些是您的主要关注点，请尝试一下。

**优点:**

*   基于 SSH，因此不需要在远程节点上安装任何代理。
*   由于使用了 YAML，学习曲线变得简单。
*   剧本结构简单，结构清晰。
*   具有变量注册功能，使任务能够为以后的任务注册变量
*   比其他工具更加精简的代码库

**缺点:**

*   不如基于其他编程语言的工具强大。
*   通过它的 DSL 执行它的逻辑，这意味着经常查看文档，直到你学会为止
*   即使是最基本的功能也需要变量注册，这会使简单的任务变得更加复杂
*   自省差。很难在行动手册中看到变量的值
*   输入、输出和配置文件的格式不一致
*   有时在性能速度上挣扎。

## 2.厨师

Chef 是一个用于配置管理的开源工具，专注于开发者端的用户群。Chef 以主-客户机模式运行，需要一个单独的工作站来控制主服务器。它基于 Ruby，你写的大部分元素都用纯 Ruby。Chef 的设计是透明的，是基于遵循给出的说明，这意味着你必须确保你的说明是清楚的。

**何时使用:**在考虑使用 Chef 之前，请确保您熟悉 Git，因为它是配置所必需的，以及 Ruby，因为您必须用它来编写。Chef 适合开发型团队和环境。这非常适合为异构环境寻找更成熟解决方案的企业。

**优点:**

*   丰富的模块和配置方案集合。
*   代码驱动的方法为您的配置提供了更多的控制和灵活性。
*   以 Git 为中心赋予了它强大的版本控制能力。
*   “刀”工具(使用 SSH 从工作站部署代理)减轻了安装负担。

**缺点:**

*   如果你还不熟悉 Ruby 和过程化编码，学习曲线会很陡。
*   它不是一个简单的工具，这可能会导致大型代码库和复杂的环境。
*   不支持推送功能。

## 3.构造

Fabric 是一个基于 Python 的工具，用于简化应用程序部署中的 SSH。它的主要用途是在多个远程系统上运行任务，但也可以用插件来扩展，以提供更高级的功能。Fabric 将配置您的系统，进行系统/服务器管理，并自动部署您的应用程序。

**何时使用:**如果您刚刚开始部署自动化领域，Fabric 是一个很好的起点。如果您的环境至少涉及到一点点 Python，那会很有帮助。

**优点:**

*   擅长部署用任何语言编写的应用程序。它不依赖于系统架构，而是依赖于操作系统和软件包管理器。
*   比这一领域的其他工具更简单、更易于部署
*   与 SSH 广泛集成，实现基于脚本的简化

**缺点:**

*   Fabric 是单点故障设置(通常是运行部署的机器)
*   使用推送模型，因此不像该领域的其他工具那样适合持续部署模型
*   虽然它是在大多数语言中部署应用程序的一个很好的工具，但它确实需要 Python 来运行，所以您必须在 Fabric 环境中至少有一点 Python。

## 4.木偶

[Puppet](https://puppet.com/) 是成熟的配置管理领域中历史悠久的工具之一。这是一个开源工具，但是考虑到它已经存在了很长时间，它已经被很好地审查并部署在一些最大和最苛刻的环境中。Puppet 基于 Ruby，但是使用了一种定制的领域脚本语言(DSL ),更接近于 JSON。它作为主客户端设置运行，并使用模型驱动的方法。Puppet 代码设计作为一个依赖列表工作，它可以使事情变得更容易或更混乱，这取决于您的设置。

**何时使用:**如果稳定性和成熟性是你的关键因素，木偶是个不错的选择。这对具有异构环境和 DevOps 团队技能范围的大型企业来说是很好的。

**优点:**

*   通过木偶实验室建立了完善的支持社区。
*   它有最成熟的界面，可以在几乎所有的操作系统上运行。
*   简单的安装和初始设置。
*   这个领域最完整的网络用户界面。
*   强大的报告能力。

**缺点:**

*   对于更高级的任务，您将需要使用基于 Ruby 的 CLI(这意味着您必须了解 Ruby)。
*   对纯 Ruby 版本(而不是那些使用 Puppet 定制 DSL 的版本)的支持正在缩减。
*   由于 DSL 和不注重简单性的设计，Puppet 代码库可能会变得很大、很难处理，并且很难为组织中的新成员所接受。
*   与代码驱动方法相比，模型驱动方法意味着更少的控制。

## 5.盐堆

SaltStack(或 Salt)是一个基于 CLI 的工具，可以设置为主客户端模型或非集中式模型。基于 Python，Salt 提供了与客户端通信的推送方法和 SSH 方法。Salt 允许对客户端和配置模板进行分组，以简化对环境的控制。

**何时使用:**如果可伸缩性和弹性是个大问题，Salt 是个不错的选择。由于它的可用性，对系统管理员来说是个好消息。

**优点:**

*   一旦你过了设置阶段，简单的组织和使用。
*   他们的 DSL 功能丰富，不需要逻辑和状态。
*   输入、输出和配置非常一致，都是 YAML。
*   自省很好。很容易看出盐里发生了什么。
*   强大的社区。
*   主模型中的高可伸缩性和弹性，带有 minions 和层次结构层。

**缺点:**

*   难以为新用户设置和挑选。
*   文档在入门阶段很难理解。
*   Web UI 比这个领域中的其他工具的 Web UI 更新，也不太完整。
*   不太支持非 Linux 操作系统。

## Ansible vs 厨师 vs 布料 vs 木偶 vs 盐堆

您使用哪种配置管理或部署自动化工具将取决于您对环境的需求和偏好。Chef 和 Puppet 是一些更老、更成熟的选项，使它们适合于更大的企业和环境，这些企业和环境重视成熟性和稳定性而不是简单性。Ansible 和 SaltStack 是那些在不需要支持古怪特性或大量操作系统的环境中寻找快速简单解决方案的人的好选择。对于较小的环境和那些寻求更低成本和入门级解决方案的人来说，Fabric 是一个很好的工具。