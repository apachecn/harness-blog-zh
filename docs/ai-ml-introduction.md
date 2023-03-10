# 人工智能和机器学习导论

> 原文：<https://www.harness.io/blog/ai-ml-introduction>

在过去的两年半时间里，我有机会在数据科学、机器学习(ML)和人工智能(AI)方面投入大量时间。这篇博文回答了我在学习 ML 和 AI 的工作、技术、术语和工具之前提出的许多问题。

## 什么是 AI 和 ML？

许多公司将他们的系统或服务宣传为“由人工智能驱动”，但实际情况并非如此。我们总是会发现这些噱头营销的实例，所以首先理解什么是人工智能和人工智能以及不同的术语是有帮助的，因为在我们今天的世界中有许多人工智能和人工智能的相关用例。

人工 **智能**是一种用于构建模仿人类行为或决策的系统的技术。

**机器** **学习**是利用数据解决任务的 AI 的子集。这些解算器是经过训练的数据模型，根据提供给它们的信息进行学习。这些信息来自概率论和线性代数。ML 算法使用我们的数据来学习并自动解决预测任务。

**深度** **学习**是机器学习的一个子集，它依靠多层神经网络来解决这些任务。

### 机器学习的形式

鉴于机器学习是人工智能的基础，理解机器学习的不同形式是值得的。

机器学习有三种:**有监督的**，**无监督的**，**强化的** **学习**。每种形式解决问题的方式不同。

### 监督机器学习

在监督机器学习中，我们知道数据和问题。把它想成，“给定一组特征 x，我们知道 y 的值，”因此在监督学习中，我们创建一个基于某组数据的近似结果的函数。

监督学习有两种:**分类**和**回归**。在分类问题中，我们将数据分配到类别中。例如，给定一个客户的医疗信息，他们测试阳性或阴性的糖尿病。在分类中，我们训练的模型，称为分类器，将数据点分类到不同的组中。

相反，如果我们想解决一个不同的问题，比如根据股票市场历史预测 GameStop 股票的未来价值，我们会转向回归。在回归中，我们返回数值。给定一些句子，这是这个人快乐或悲伤的可能性百分比。

### 无监督机器学习

在无监督的机器学习中，我们的数据是无标签的。无监督机器学习有两种形式:**聚类**和**维数** **约简**。

在聚类中，当数据点被聚类或分组在一起时，我们会了解更多关于它们的信息。这使得学习过的模型能够理解数据集，检测异常，并分配点之间的关系，通常允许用户开发关于数据集的新类别或特征。

在降维中，我们绘制不同维度和特征集的数据点，以了解我们的数据集。这允许像特征选择或转换这样的技术。降维解决了维数灾难。数据集的特征越多，需要的数据就越多，处理许多有噪声的特征会影响 ML 模型的性能，因此无监督的机器学习技术通常与监督或强化学习算法配对。

### 强化学习

在强化学习(RL)中，我们随着时间的推移学习模型。一种常见的技术是利用深度学习和强化学习来推导数据集特征之间的关系，否则可能无法通过人类研究来解决。深度学习 RL 最近在医学领域非常成功。

## 人工智能的用例

从交通、医药、，到计算机视觉，ML、AI 对市场资本产生了全球性的影响。最近的一项研究也证实，在未来，深度学习将比互联网产生更多的市场资本。

也就是说，人工智能在软件开发和 IT 运营领域也有许多应用，包括人工智能驱动的可操作化、下一级交付洞察和人工智能增强的开发。在 SaaS 和云提供商的时代，这些方面肯定是相关的。下图显示了与人工智能和人工智能用例相关的不同角色的案例。一个解决方案可以是一个数据源，一个 AI/ML 学习者，一个决策者，或者是这三者的组合。

### AI 和 ML 的 DevOps

注意 AI 和 DevOps 之间的关系是双向的，这一点很重要。AI 和 ML 不仅影响 DevOps，反过来也是如此。MLOps 努力使 ML 模型的交付安全、可重复且快速。 [Kubeflow](https://www.kubeflow.org/) 是一个将 ML 和 AI 解决方案推向市场的解决方案的例子，其卓越之处在于 DevOps 的实践、原则和文化。

如果我们想更好地理解这个管道的一部分，最好是利用 Python 中的 SKLearn 库来了解一个简单的分类问题。

## 在 Python 中准备数据和训练模型

由于数据收集过程或使用的仪器，一些信息字段可能会丢失或不准确。数据湖、数据仓库和数据库都是存储数据的相关方法。因此，数据科学家有时会与领域专家一起提取数据，并为 ML 模型或算法进行预处理。

在这个例子中，我们从一个 CSV 文件中读入一些数据，并使用 pandas 和 NumPy 库标记这些特性。这个数据集是一个流行的[糖尿病数据集](https://archive.ics.uci.edu/ml/datasets/diabetes)，它包含了华盛顿大学研究人员获得的糖尿病患者记录。

https://gist。github。com/tiffanyjachja/8 ce 99 DD 0 ef 3772 ab 1736 F8 a2 b 32956 FD

如代码片段所示，我们正在读取数据集并过滤掉任何缺失的值。这个数据集是通过自动电子记录设备获得的，所以有些字段丢失了。通常情况下，特定要素的平均值将替换任何缺失值。这个数据集也是如此，包括血压等特征。

#### **培训一名 ML 模特**

在数据被清理并准备好进行处理之后，整个数据集被分成训练集和测试集。验证集用于训练过程，以确保模型不会过度拟合数据。[过度拟合](https://elitedatascience.com/overfitting-in-machine-learning)会导致一些问题，比如在训练集之外的数据上表现不佳。

该训练集数据用于学习过程。对于这个预测糖尿病患者的分类问题，学习过程是基于函数逼近的，如下图所示。

下面是分割数据和训练决策树分类器的代码。

现在我们有了训练好的模型和结果，我们可以评估模型的性能和准确性。如果一切顺利，这种模式可以出口或部署消费！

## 下一步是什么？

这篇博文展示了 AI 和 ML 的一些简单用例。在这个领域还有许多其他相关的解决方案、工具和库。我希望这能让你很好地了解这个主题，以便你能够更深入地了解更多关于 AI 和 ML 的知识。

感谢阅读。这个内容实际上是基于我在 2021 年北美 DevOps 集团的开发者会议上的演讲。如果你喜欢这种指南，并且想要更多的 AI/ML 内容，请告诉我！干杯！