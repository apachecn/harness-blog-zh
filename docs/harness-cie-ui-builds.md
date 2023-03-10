# 为 UI 构建利用 CIE:了解如何构建管道

> 原文：<https://www.harness.io/blog/harness-cie-ui-builds>

让我们回顾一下如何创建 CIE 管道(以及我们如何创建自己的管道)，并回顾一下缓存策略。

这篇文章向您展示了创建一个 Harness CI Enterprise (CIE)管道的过程，以及我们如何使用它来创建我们自己的 UI 构建管道。我们还将介绍所使用的缓存策略，它确保了更快的作业执行。

## CI 是什么？

在开始线束 CIE 之前，我们先了解一下什么是 CI。

持续集成(CI)是将来自多个参与者的代码变更自动集成到一个软件项目中的实践。集成过程可以通过一些特定的工具来自动化，这些工具根据需要频繁地使用脚本和过程。这意味着新代码的兼容性正在被自动测试。此外，这支持早期发现的集成错误。此外，单元测试或系统级测试可以自动完成，无需任何开发人员的干预。如需了解更多信息，请查看我们的[什么是持续集成？](https://harness.io/blog/what-is-continuous-integration/)岗位。

## 为什么要利用 CIE？

就 CI 而言，有许多工具可用，但主要缺点是这些工具涉及相当多的手动脚本编写，CI 和 CD 之间的集成很少。这些工具在 CI 领域的一个流行例子是 Jenkins。

Harness 提供了一些很棒的特性，比如**测试智能**、**和**，通过只运行确认触发构建的代码更改的质量所需的测试，显著减少了测试时间。

在 Harness，我们使用 [Kubernetes](https://kubernetes.io/) 作为构建场来运行我们的 CI 构建工作。在 Kubernetes 中，管道步骤在容器中运行，容器是主机操作系统的轻量级抽象，可以独立于步骤打包代码和依赖项。此外，我们不需要担心依赖性，因为所有的步骤都在容器中运行，插件有它们自己的容器。

线束 CIE 还提供了具有嵌套步骤的管线的图形表示。直接从用户界面构建，或者使用 YAML 编辑器。YAML 编辑器的功能类似于 IDE，您可以轻松地将其配置为代码。

## 我们如何利用 CIE 来为 UI 构建创建管道

四个简单的步骤创建并执行 CIE 管道:

1.  创建新管道，并在创建管道阶段时克隆代码库
2.  定义构建场基础结构
3.  添加执行步骤
4.  运行管道

**“CI”模块中的“创建管道”**将用户带到 Pipeline studio，然后我们在那里添加阶段。我们可以通过组合不同的 CI 步骤来创建多个阶段。每个阶段都包括构建、推送和测试代码的步骤。

因此，我们可以在一个管道中为 PR 检查并行创建多个阶段，也可以为每个 PR 检查创建单独的管道。

代码库克隆的主要先决条件是安装一个 Harness 委托。代理负责所有的 Harness CIE 操作，它将 Harness Manager 连接到所有的代码库、工件、基础设施和云提供商。

**克隆代码库**的主要行动项目是:

*   创建 GitHub 连接器
*   用代码库将线束连接到 GitHub repo

为了**定义构建农场基础设施**，我们必须选择一个 Kubernetes 集群(或者创建一个 Kubernetes 连接器)。此连接器将线束连接到集群以用作构建场。

在名称空间中，我们必须输入要使用的 Kubernetes 名称空间。

**流水线执行步骤**被定义为一系列用于执行动作的命令。例如，运行和运行测试步骤在容器映像上执行一个或多个命令。这些命令在 git 存储库的根目录下运行。管道阶段中的所有步骤共享您的 Git 存储库根，也称为工作区。在 Harness CI 中，我们可以添加一个步骤或步骤组合，以创建符合您特定需求的管道。

## 缓存策略

在为 UI 构建 PR 检查配置管道时，我们使用了 Harness 中的缓存机制。缓存通过重用先前作业中昂贵的获取操作数据来确保更快的作业执行。

在 Harness CIE 管道中，我们可以在一个阶段中使用“将缓存保存到 S3”步骤将缓存保存到[亚马逊简单存储服务(S3)](https://aws.amazon.com/s3/) 桶，并在同一个或另一个阶段中使用“从 S3 恢复缓存”步骤恢复缓存。

Harness 还提供了将缓存保存到 GCS 和从 GCS 恢复缓存的步骤。

我们在配置 PR 检查管道时使用的执行步骤按以下顺序执行:

1- **获取散列**:为了获取散列，我们使用运行执行步骤，在这里我们可以添加定制脚本。对于这个例子，我使用 docker-hub 注册中心的 node:16 映像来运行这个步骤的定制脚本。我们使用***` OpenSSL sha1 yarn . lock | cut-c 22-`****来获取纱线锁散列，并使用输出变量来公开散列。这让我们可以存储缓存。*

*2- **恢复缓存**:下一步是恢复缓存。在保存缓存或安装节点模块步骤之前添加此步骤，以检查缓存是否已经存在，并从那里恢复它。为此，我们只需要一个亚马逊 S3 或 GCS 桶来存储缓存。我们根据一个键保存缓存。我们在示例中用来存储缓存的键是:***node modules-$ { outputVariable }***，其中 output variable 是我们在上一步中用来公开 ***YARN_LOCK_HASH*** 的变量。*

*3- **安装节点模块**:下一步是安装节点模块。我们将添加脚本来将 Harness CIE 连接到 npm 注册表。然后，添加 ***纱*** 脚本来安装节点模块。*

*4- **保存缓存**:安装节点模块后，我们必须将文件/文件夹保存在缓存中。这意味着它可以在下次执行时从缓存中恢复。在配置保存缓存步骤时，我们应该确保保存缓存所针对的 Amazon S3/GCS 存储桶、区域和键应该与恢复缓存步骤的相同。如附图所示，源路径是要缓存的文件/文件夹列表。在我们的例子中，它是 ***节点 _ 模块*** 。*

*5- **执行构建的运行步骤**:配置我们的 UI 构建以进行 PR 检查的最后一个执行步骤是添加运行步骤。在这里，我们可以添加自定义脚本来执行特定的 PR 检查，比如 ES Lint、appellister 或 Jest。我们再次添加了将线束 CIE 连接到 npm 注册表的脚本，随后添加了使用 ***yarn lint*** 运行 ESLint 作业的脚本。*

*请注意，在配置步骤时，即使从缓存恢复步骤失败，管道也不会失败，这是线束管道的默认行为。*

*要实现这一点，必须在安装节点模块步骤(在“高级”选项卡中)中选中 ***始终执行此步骤*** ，并在安装节点模块之后的步骤中添加***<+execution . steps . Install _ Node _ modules . status>= " SUCCEEDED "***条件(如下图所示)。*

## *查看您的管道执行情况*

*在我们完成配置部分之后，剩下的唯一一步就是保存和运行管道。我们可以在执行阶段细节或控制台视图中查看结果。*

## *性能至关重要*

*在前面的章节中，我们讨论了缓存可以提高管道执行的性能。让我们试着用下面的例子来理解同样的事情。*

### *场景 1*

*在这个场景中，我们不从缓存中恢复文件，而是安装整个节点模块。这需要 5m 2s 来完成流水线执行。*

### *场景 2*

*在这个场景中，缓存存在于存储桶中，我们从缓存中恢复节点模块。这次执行只用了 1 分 25 秒。*

*这只是一个非常简单的管道的例子。然而，对于具有许多阶段和步骤的管道，缓存和非缓存策略之间的差异是显而易见的。*

*将这种缓存策略应用于为 Harness private repository 运行的作业，为我们的 UI 构建节省了大约 10 分钟的时间。在我看来，这是一个很好的成功标准。*

*使用缓存策略还可以让我们节省网络带宽。我们每天在 Harness 运行数百个 CIE 任务。因此，如果我们必须通过网络为每个作业下载平均大小为 1 GB 的压缩节点模块，那么想象一下这个任务消耗的网络带宽量。此外，通常我们的节点模块不会得到更新。反过来，缓存策略节省了额外的网络带宽。*

## *结论*

*感谢您花时间阅读这篇文章，并理解如何为 UI 构建创建线束管道。在这篇文章的结尾，我非常希望你现在可以建立自己的线束 CIE 管道。*

*如果你想了解更多关于 CI 的知识，请阅读我们如何从 [Jenkins 迁移到利用 CIE](https://harness.io/blog/jenkins-to-cie-journey/) 和[亲自尝试](https://app.harness.io/auth/#/signup/?module=ci)。要了解更多关于线束 CIE 的信息，请参见[线束 CIE 文档](https://ngdocs.harness.io/category/zgffarnh1m-ci-category)！*