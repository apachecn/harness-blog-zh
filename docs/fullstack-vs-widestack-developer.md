# 什么是全栈部署自动化？装具

> 原文：<https://www.harness.io/blog/fullstack-vs-widestack-developer>

你还记得 fullstack developer 这个术语开始流行的时候吗？

## fullstack 对 widetrack 开发者

你还记得那个时候术语 [fullstack 开发者](https://skillcrush.com/2017/02/27/front-end-back-end-full-stack/)开始兴风作浪吗？一个 [fullstack 开发者](https://skillcrush.com/2017/02/27/front-end-back-end-full-stack/)是一个软件工程师，他拥有一个 web 应用程序的前端和后端组件。他们曾经是(现在仍然是)现代软件开发世界的独角兽。[全球 51.9%的开发者](https://insights.stackoverflow.com/survey/2019#developer-roles)认同 fullstack，在 2019 StackOverflow 开发者调查中位列大多数开发者。

然而，一只新的独角兽来了。随着软件开发变得越来越简单，开发人员的责任也增加了，包括他们代码的整个生命周期。widestack 开发人员是 fullstack 开发人员的现代版本，因为他们拥有应用程序堆栈的开发、部署、操作和监控。换句话说，当 fullstack 开发者拥有更多他们正在构建的东西时，widestack 开发者也拥有更多将他们的代码投入生产的东西。

widestack 开发人员是 fullstack 开发人员的现代版本，因为他们拥有应用程序堆栈的开发、部署、运营和监控

## 全栈开发者

传统上，fullstack 开发人员拥有其应用程序堆栈的前端组件和后端组件。例如，web 应用程序将包含以下内容:

*   前端
*   超文本标记语言
*   半铸钢ˌ钢性铸铁(Cast Semi-Steel)
*   java 描述语言
*   jQuery
*   后端
*   Linux 操作系统
*   关系型数据库
*   计算机编程语言
*   Nginx

*全栈开发*

这将是启动和运行整个应用程序的基本组件。你不仅要理解一门编程语言，还要理解它执行的环境:操作系统、数据库和 web 服务器。因为您的应用程序正在输出所有的客户端代码(例如 HTML)，所以您也将开始拥有所有的客户端逻辑。这就是 fullstack 开发人员的由来。自然地，更成熟、更有经验的工程师接管了整个堆栈。

谁从中受益了？优点是:

*   更快的开发周期
*   所有权方面的困惑更少
*   更少的错误
*   更快地解决应用程序问题

经济学是清楚的。fullstack 开发者曾经是/现在是每个公司都在追逐的独角兽。

## 宽堆栈开发人员

在当今的现代应用程序生态系统中，组织拥有数十个、数百个甚至数千个在后端运行的服务来实现应用程序的功能。因此，开发人员不再像关注“宽堆栈”那样关注“全堆栈”换句话说，开发人员对拥有更多他们的环境不感兴趣，他们更感兴趣的是拥有部署他们代码的完整操作。

历史上，作为一名开发人员，我只编写代码并将其签入 Git。就这样。我相信这个过程足够好，知道在我的代码进入生产时该怎么做。今天，我对这个过程有了更多的了解。为什么？因为开发变得如此简单。我给你举几个例子。

## 再见 IT 运营部

世界被引入弹性云托管环境。基础设施、计算能力和服务器资源不再是问题。开发人员可以轻松管理他们的基础设施，而不需要传统的运营团队。您可以轻松地上下旋转服务器，并且可以大规模进行。操作科学已经被抽象在 AWS、Azure 和 Google Cloud 提供的一个非常小的 UI 中。我可以使用 Terraform 和 Ansible 等工具大规模配置我的基础架构。我可以使用像 Chef 或 Puppet 这样的工具来配置我的部署环境。我可以使用 Docker、Kubernetes 和 Helm 等工具打包、维护和配置我的微服务。

## 再见性能工程师

监控您的软件也变得更加容易。利用应用运行时和成熟的 APM 工具(如 AppDynamics、New Relic)可以轻松监控、检测和诊断生产中的应用问题。当错误蔓延到生产中时，我已经对错误进行了全面的诊断，一直到代码行。

我不必等到流量冲击我的生产应用程序，因为我可以使用 Synethic 监控工具在它们影响客户之前嗅出我的错误。

见鬼，为什么还要等到生产呢？

我可以使用混沌工程技术来复制灾难场景，并在我的应用程序和操作中建立弹性。我可以利用生产前测试，模拟最坏情况下的生产噩梦，以确保只有防弹代码和可扩展系统才能进入生产，并最终进入我们的客户。

## 再见质量保证工程师

可以在多个层上快速测试代码的自动化测试套件的引入，使开发人员能够轻松地编写和测试他们的软件。开发人员和 QA 的职责不再分离。QA 工程师现在可以加入开发团队的其他成员，专注于增值功能，而不是全职专注于 QA。

一旦构建了一个特性，该特性的测试也就编写好了。当特性投入生产时，自动化测试覆盖已经存在，以确保最佳性能。

## 再见，手动发布脚本

老实说，还有什么比手动编写和维护部署管道更痛苦的呢？幸运的是，整个 CI/CD 流程是通过完全自动化整个流程的现代平台抽象出来的。自动化 CI/CD 流程的结果是，开发人员现在完全可以自主部署他们自己的代码。

“自动化 CI/CD 流程的结果是，开发人员现在完全有能力自主部署他们自己的代码。”

我不是说在这里插线束，但我肯定是要在这里插线束。使用 Harness，您可以轻松地将您所依赖的所有痛苦的手动脚本抽象到完全自动化的 CD 管道中，从而快速地将您的服务部署到生产中。最终的结果是，大型组织中的数千名开发人员现在被解放出来，完全自主地部署他们的代码。

## 证据在哪里？

为了证明我的观点，我使用 [stackoverflow](https://stackoverflow.com) 搜索了一个“全栈开发者”。我发现下面的帖子有明确的陈述，表明了 widestack 开发人员的明显趋势。每一份招聘启事都清楚地表明他们招聘的角色拥有整个软件开发生命周期。每个项目符号都是职位描述的一部分，申请人必须了解并有相关经验。

[瓦瓦托](https://stackoverflow.com/jobs/328650/full-stack-developer-vavato?so=i&pg=1&offset=1&q=full+stack+developer):

*   我们使用连续交付，每天多次部署到生产环境，零停机时间。
*   我们在看板和发布特性准备好的时候使用它们，从来没有做过大爆炸式的发布，也没有创建“一个发布”。
*   连续交货的经验。

[查里迪](https://stackoverflow.com/jobs/307185/full-stack-developer-charidy?so=i&pg=1&offset=5&q=full+stack+developer)

*   拥有代码版本管理工具(Git)和现代全栈构建管道和工具的经验

[PropertyGuru 私人有限公司](https://stackoverflow.com/jobs/297394/full-stack-engineer-propertyguru-pte-ltd?so=i&pg=1&offset=7&q=full+stack+developer)

*   设计模式、单元测试、自动化技术方面的经验(Selenium WebDriver)
*   接触亚马逊网络服务(EC2、S3、EBS、RDS、SQS、红移等。)
*   接触 Scrum 方法和 XP 技术实践，如单元测试、结对编程、测试驱动开发、持续集成或持续交付

[山脊线国际公司](https://stackoverflow.com/jobs/336959/full-stack-software-engineer-ridgeline-international-inc?so=i&pg=1&offset=10&q=full+stack+developer)

*   对 Git、Jenkins 和 Docker 的 DevOps 有深入了解者优先

[提升](https://stackoverflow.com/jobs/355865/full-stack-software-developer-ascension?so=i&pg=1&offset=-1&q=full+stack+developer)

*   创建单元和集成测试来全面测试和回归软件
*   对完整 SDLC 的专业软件工程最佳实践有深刻的理解，包括编码标准、代码审查、源代码控制、构建流程、测试和操作
*   展示对完整 SDLC 的掌握，包括 CI/CD 和现代构建和部署工具

## 不可能，作战永远不会消失

嗯，你可能是对的...短期内。您还记得系统管理员不得不手动更换和升级 CPU 的时代吗？还是用 CAT5/6/7/8 线缆插电连接网络交换机？

美好时光，对吧？

不。绝对不。当然不。那不是好时光。

即使他们是，你也肯定不记得他们，因为你可能还没有高中毕业。那是在你出生之前。

技术变化。它会进化。职责继续被隔离，变得抽象，并消失在某个数据中心或一个复杂的新平台的深渊中，该平台的出现使事情变得更容易和更好。那么现代堆栈有什么不同呢？有一个轨迹暗示了持续的抽象和减少的部署障碍。你所要做的就是把这些点联系起来，你很容易就能看出一个趋势。

## 马具

如果您对自动化部署管道感兴趣，可以尝试一下 Harness。你会惊奇地发现，你可以轻而易举地做一些很酷的事情，比如:

*   自动化金丝雀测试
*   使用您现有的 APM 工具进行自动化验证
*   使用 YAML 配置管道的 Gitops 配置
*   还有很多。

[注册免费试用](https://harness.io/)！