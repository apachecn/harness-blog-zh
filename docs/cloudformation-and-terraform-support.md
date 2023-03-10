# 云形成和地形形成-添加基础架构供应器|线束

> 原文：<https://www.harness.io/blog/cloudformation-and-terraform-support>

你使用 CloudFormation 和 Terraform 脚本/模板吗？Harness 在我们的部署管道模型中引入了基础设施供应器。

基础架构供应器对于云原生应用和环境来说是一件大事。自动化基础架构的配置和停用使您能够即时扩展和缩减，同时获得按需计算的成本优势。

通过将此流程集成到所有环境的部署管道中，您可以有效地扩展端到端自动化，并为所有开发和工程团队获得成本优势。

例如，仅当新的构建或版本存在或需要测试时，才启动开发、QA 和准备[环境](https://harness.io/blog/deployment-environments/)。当您需要复制生产时，您还可以使用它们进行快速[蓝绿](https://harness.io/blog/blue-green-canary-deployment-strategies/)部署。

在过去的一年里，我们不断从客户那里听到 AWS CloudFormation 和 HashiCorp Terraform 是新的标准；因此，与 Harness 软件交付平台的集成是“不需要动脑筋的”

## 什么是 AWS CloudFormation？

[AWS cloud information](https://aws.amazon.com/cloudformation/)为您提供了一种通用语言来描述和调配云环境中的所有基础架构资源。

CloudFormation 允许您使用一个简单的文本文件，以自动化和安全的方式，跨所有地区和客户对您的应用程序所需的所有资源进行建模和供应。该文件是您的云环境的唯一真实来源。

## 什么是 HashiCorp Terraform？

[HashiCorp Terraform](https://www.terraform.io/) 使您能够安全、可预测地创建、更改和改善基础设施。它是一个开源工具，将 API 编译成声明性的配置文件，可以在团队成员之间共享，作为代码处理，编辑，审查和版本控制。

Terraform 类似于 AWS CloudFormation，但它是多云的——这意味着它是定义跨 AWS、Azure、GCP 等基础设施的通用语言。

## 引入线束“基础供应器”

为了适应 CloudFormation 和 Terraform 脚本/模板，我们在部署管道模型中引入了一个名为“基础设施供应器”的新概念:

可以将基础架构供应器添加到任何部署工作流中，以便在部署过程中供应和停用基础架构(云集群)(如果需要)。

其理念是，您可以跨部署工作流和管道轻松地重用、管理、调试和编排 CloudFormation 和 Terraform 脚本/模板。您的基础架构与应用程序级别上发生的事情保持同步。

## 创建基础架构置备程序

进入**设置>你的应用>基础设施提供者**
点击 **+添加基础设施提供者**，选择**地形**或**云形成。**

接下来，添加您的脚本/模板的主体，或者通过源类型下拉菜单简单地引用它:

您可以通过按下**从模板**控件填充来自动解析来自脚本/模板的输入变量，或者您可以使用 **+Add** 控件手动创建它们。

接下来，您需要将每个基础设施供应器映射到一个或多个服务(工件)。点击**添加服务映射**，选择需要的服务、部署类型和云账户。然后，您可以使用$前缀指定适当的集群配置，作为文本或变量；这基本上允许您将参数从 CF/Terraform 传递到线束工作流程&环境中。

您的基础架构供应器设置现已完成:

## 向部署工作流添加基础架构设置程序

一旦定义了基础架构供应器，现在就可以在任何部署工作流中添加和引用它们。

例如，下面是一个简单的 canary 部署工作流，分为三个阶段。

我们可以通过在工作流程中添加**预部署步骤**来轻松添加/引用我们的 CloudFormation 或 Terraform 脚本/模板:

该控件显示以下对话框，我们可以在其中将 CF/TF infra provisioner 添加到工作流中:

现在，除了脚本/模板变量之外，您还可以使用相关的云提供商详细信息实例化您的 CF/TF 脚本/模板，这些变量可以是带文字的静态变量，也可以是带参数的动态变量。

添加后，您的工作流将如下所示，显示您的**基础配置程序**将在部署阶段之前执行:

如果您也想使用 CF/TF 来淘汰基础设施，您也可以将其作为**部署后步骤**。

## 调试云形成和地形部署

现在，当您执行管道或部署工作流时，您将在部署上下文中看到所有 CloudFormation 和 Terraform 控制台输出。这对于调试和管理任何基础架构供应问题非常有用:

我们努力让客户尽可能简单、轻松地将 CloudFormation 和 Terraform 集成到他们的部署管道中！

这里有一个两分钟的视频展示了这有多简单:

您可以从 Harness 软件交付平台的[免费试用版](https://app.harness.io/auth/#/signup)开始。
干杯，
史蒂夫。@ BurtonSays 说