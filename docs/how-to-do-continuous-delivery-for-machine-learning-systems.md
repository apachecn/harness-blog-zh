# 机器学习系统的持续交付|线束

> 原文：<https://www.harness.io/blog/how-to-do-continuous-delivery-for-machine-learning-systems>

使数据科学家、数据工程师和 ML 工程师能够围绕数据管理、模型培训、部署和操作化扩展他们的流程。

## ML 系统的挑战

在 ML 的软件工程领域出现的许多著名的研究论文都是关于构建[可维护的应用程序](https://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems.pdf)以满足不断变化的最终用户需求的主题。连续交付使所有类型的软件变更能够以安全、快速和可持续的方式到达生产环境。

为了使数据科学家、数据工程师和 ML 工程师能够围绕数据管理、模型培训、部署和操作化扩展他们的流程，我们将分解 ML 持续交付所需的组件。

生产 ML 系统是一个大的生态系统，包含三个主要部分:数据、模型和为消费者提供模型输出的代码。这个生态系统的每一个元素都需要精心呵护和维护才能达到生产目的。

通常，对数据集所做的更改会对创建 ML 模型的数据科学家以及 ML 工程师如何整合更改产生影响。下面是一个倾向于出现的常见功能孤岛的图示。

[Common functional silos in large organizations can create barriers, stifling the ability to automate the end-to-end process of deploying ML applications to production](https://martinfowler.com/articles/cd4ml.html).

大型组织中的传统功能孤岛会造成障碍，抑制将 ML 应用程序部署到生产的端到端流程的自动化能力。

## 定义您的 CD 管道

为现代 ML 服务定义一个部署管道。您需要处理数据、模型和代码的工作流。由模块化工作流组成的管道可以在未来的部署中重用和修改。以下是典型部署管道的步骤:

1.  写代码
2.  提交代码
3.  构建工件
4.  测试工件
5.  部署工件
6.  验证工件
7.  回滚工件

让我们来讨论 ML 系统管道的步骤。

**第一步:建立可发现和可访问的数据**

这个步骤的最终状态是一个版本化的、可发现的和可访问的数据工件。创建一个工作流，在数据集上运行数据清理和预处理，以生成存储在存储库中的工件。您可以利用您的 Jenkins 管道来触发这一过程。为下一阶段将工件引入您的环境。

**第二步:模型训练**

您的管道应该包括模型培训和测试的工作流程。回想一下，工作流自动化了三件事情:服务的部署、服务的测试和验证，然后回滚(如果需要的话)。考虑以下模型训练工作流:

1.  拉出数据工件
2.  运行将数据拆分为定型集和验证集的函数
3.  根据训练数据生成模型

为下一步生成模型工件。

**第三步:真实世界曝光**

我们制作了一个模型产品供消费者使用；现在，是时候部署模型了。为模型提供服务有许多策略，包括将模型嵌入到现有的应用程序服务中，将模型作为单独的服务进行部署，或者在运行时将模型发布到服务数据。无论哪种模式都会创建一个包含以下工作流模型的可部署工件:

1.  将所述工件部署到环境中，定义发布策略
2.  测试、验证和确认最新的模型
3.  如有必要，回滚

添加额外的步骤和阶段，以将工件提升或部署到更高的环境中。

创建分离数据、模型和代码的工作流为您提供了健壮和有效的 ML 管道的构建块。向任何工作流程添加更多步骤，以进一步验证和测试您的 ML 系统。

## 其他考虑

我们描述了 ML 系统的端到端生产管道的准系统模板。在角色需要分离关注点的情况下，创建额外的工作流和管道会很有用。执行部署或验证步骤，而不触发整个生产管道。以下是一些附加的试衣场景，将被纳入你的持续交付渠道。

**数据新鲜度:**

对于数据新鲜度对模型的准确性至关重要的用例，持续的数据收集。创建一个单独的管道，部署一个服务来收集、组织和生成最终数据集。收集正确数据传递的有效验证步骤和测试，并将其构建到您的管道中。这给了您的数据工程团队对他们的数据变更和修订的所有权。

**验证:**

您应该有模型性能的标准或阈值。利用您的监控工具与您的 CD 管道集成，实现管道中内置的自动验证。监控工具和仪表板暴露了用于持续验证的 API 端点或插件。这样，您可以确保在最新数据集上训练的模型的质量。

**回滚:**

通过失败标准触发回滚。您可以使用回滚来触发管道，该管道将使用最新数据重新训练您的模型。

## 结论

连续交付(CD)使所有类型的软件变更能够以安全、快速和可持续的方式到达生产环境。我们的目标是使部署在任何体系结构中都是可预测的、常规的，这样开发人员就可以按需执行部署。这给了团队在不破坏事物的情况下创新和快速行动的自由。

我们讨论了机器学习系统持续交付的从头到尾的模板。像 Tensorflow 这样的工具有助于增强持续交付模型所需的工作流。当自动化端到端流程时，必须考虑定义基于云、代码或框架的部署的未来成本和灵活性。我们还讨论了在自动化这个过程时要考虑的其他场景。我希望这篇博文，包括对你的连续交付 ML 管道的见解。了解有关 Harness 和我们的[软件交付平台](https://harness.io/platform/)的更多信息。