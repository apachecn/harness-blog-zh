# Kubernetes 和 Harness | Harness 的蓝绿色部署

> 原文：<https://www.harness.io/blog/blue-green-deployments-with-kubernetes-and-harness>

如何使用 Harness 平台使 Kubernetes 中的蓝绿部署变得简单。建立 CD 管道，利用线束在几分钟内完成部署。

部署到生产环境有点像在酒吧里喝醉了跳舞。您必须这样做，但这一切都是为了在一天结束时避免附带损害(和停机时间)。持续交付有多种[部署策略](https://harness.io/blog/blue-green-canary-deployment-strategies/)。蓝绿色部署和[金丝雀部署](https://harness.io/blog/build-canary-deployment/)如今往往是最常见的。

## 什么是蓝绿部署？

蓝绿色是指两个相同的环境，分别叫做“蓝色的”(也叫准备阶段)和“绿色的”(也叫生产阶段)，同时运行不同版本的服务/工件。QA 和 UAT 通常在蓝色环境中完成。当满意时，流量从绿色环境(当前版本)翻转(通过负载平衡器)到蓝色环境(新版本)。然后，如果部署成功或失败，您可以选择停用旧环境或回滚到旧环境。

在这篇博客中，我们将使用 [Kubernetes](https://kubernetes.io/) 和 Harness 构建一个蓝绿色部署。

## 步骤 1:创建新的应用程序

转到:**Setup>Applications>Create New Application**
创建一个新的应用程序(管理服务和工件的逻辑组)应该需要**10 秒钟的时间**。

## 步骤 2:创建新服务

显然，我们需要一些东西来部署，所以让我们创建一个新的服务。

进入:**设置>您的应用>添加服务**

输入“我的微服务”作为服务名，选择“Docker Image”作为工件类型。接下来，通过引用存储库中的特定工件来添加工件源。这需要 20 秒钟。

## 步骤 3:创建新环境

显然，我们现在需要一个地方来部署我们的新服务和工件。

进入:**设置>您的应用>添加环境**

将您的环境命名为“production ”,并选择“Production”作为环境类型。接下来，单击“添加服务基础架构”，选择“我的微服务”作为您的服务，然后选择“Kubernetes”作为部署类型。接下来，选择支持 Kubernetes 的云提供商帐户，以及要部署到的集群。这个过程需要 20 秒钟。

## 步骤 4:创建蓝绿色部署工作流

工作流告诉 Harness 如何将服务部署到环境中。

转到:**设置>您的应用程序>添加工作流**

命名您的工作流，选择“蓝绿色部署”作为工作流类型，然后选择您刚刚创建的环境(生产)以及服务(我的微服务)和服务基础架构(Kubernetes 集群)。这应该会花费你 10 秒钟。

## 步骤 5:配置您的蓝绿色部署

blue-green 部署所需的大多数默认设置和配置都是现成的。唯一的要求或先决条件是您正在使用 Kubernetes 来部署您的服务构件。

例如，默认情况下，我们将在您的蓝色(暂存)环境中启动与绿色(生产)环境中已经运行的相同数量的实例。如果需要，您还可以为 Kubernetes HPA 和入口规则添加可选配置(屏幕截图中的#1)。

Harness 的最大优势在于，您可以在上面的步骤 3 中自动验证(健康检查)您的蓝绿色部署。一旦您在您的蓝色(暂存)环境中设置和部署了容器，您就可以使用您现有的 APM 和日志管理工具运行[持续验证](https://harness.io/products/continuous-delivery/)，以便您可以验证您的蓝色暂存部署。

也可以在验证完成后添加手动批准。这允许您在准备就绪时手动“拨动开关”，以便所有流量从绿色环境(当前版本)定向到蓝色环境(新版本)。还可以添加回滚步骤(上图的右上方),这样，如果将来部署失败，您可以再次将开关翻转回来。

蓝绿色的部署工作流也可以用变量“模板化”,以便其他开发团队可以重用它们。例如，您可以引入**工件**和**环境**作为工作流变量，稍后每个开发团队可以使用 CURL 或 webhooks 在部署时注入这些变量。我们的许多客户创建**黄金模板**用于部署，然后使用 RBAC 将这些模板分配给每个开发团队进行推广和扩展。创建一次，部署多次通常是最佳实践，而不是为每个工件和环境拥有单独的部署工作流。

## 第六步:运行你的蓝绿色工作流程

一旦您配置了蓝绿色部署工作流，您就可以将其附加到线束管道或触发器以供执行。

当您的蓝绿色部署正在运行时，它将看起来像这样:

报名参加 Harness 平台的[免费试用](https://app.harness.io/auth/#/signup)，在几分钟内构建自己的蓝绿色部署。

干杯！

史蒂夫(男子名)

@伯顿说