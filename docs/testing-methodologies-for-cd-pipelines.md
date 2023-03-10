# 测试方法|线束

> 原文：<https://www.harness.io/blog/testing-methodologies-for-cd-pipelines>

测试。一个能让你的开发者产生爱恨情仇的词。

## 你的 CD 管道的关键部分

测试。一个能让你的开发者产生爱恨情仇的词。就像开发和操作的小仓库一样，在过去，开发团队和质量保证团队之间有更多的小仓库。如今，在现代开发团队中，这种敌对关系正在 QA 团队中消失，一个很好的例子就是测试角色中的 SDET(T1)或软件开发工程师。SDETs 是高度专业化的工程师，为团队提供测试自动化策略/覆盖和补救专业知识。

在我的学术和早期职业生涯中，我曾经将开发排在质量保证和 QA 团队之前，认为这是一个“阻碍我进步”的团队，寻找各种各样显然永远不会发生的不可靠的错误。我从事软件开发的时间越长，对 QA 团队的尊重就越大，随着[同行编程](https://en.wikipedia.org/wiki/Pair_programming)的出现，我掌握了推动测试向前发展所需的技能。

像技术的许多方面一样，测试可以有广泛的用途。当开发一个特性时，作为软件工程师，我们在迭代创建的同时不断地执行这个特性。一旦我们在头脑中获得了正确的特性，传统的方法是将该特性送去测试。在现代开发组织中，我们不断地测试，甚至我们在开发时的行为是最终一致地测试特性。虽然测试通常分为两类，你做了什么和你所做的影响。

### 两桶

测试通常可以遵循两个阶段中的一个。第一个阶段是测试你做了什么，比如特性测试。第二个阶段是测试你产生了什么影响，例如集成/系统测试。这两个范畴可能非常广泛，例如，环境和性能测试可能属于这两个范畴，这取决于您是在构建应用程序基础架构，还是只对应用程序进行更改。通常在你的特性走向生产的过程中，你会测试你做了什么，然后测试它的影响。

### 你做了什么

软件开发当然是一项主动性的工作。我们可以用激光聚焦的方法让我们的大脑正确运作。即使是写得最好的设计文档也仍然要由开发人员来解释。作为人类，我们是我们经验的总和，我们以不同的方式解释事物。为了确保我们都在同一页上，有能力客观地测试你创造的杰作是很重要的。

#### 代码覆盖率

当谈论质量时，第一个度量标准是[代码覆盖率](https://en.wikipedia.org/wiki/Code_coverage)。通常以百分比来度量，代码覆盖率是测试期间执行的源代码的度量。有几种度量，如功能或条件覆盖。代码覆盖率通常关注我们写了什么和利用了什么；深入覆盖第三方开源代码可能会很困难，因为我们假设质量和功能达到了一定的水平。

#### 单元测试

代码覆盖是正在执行的[单元测试](https://en.wikipedia.org/wiki/Unit_testing)的集合。单元测试关注于方法/模块的执行，例如我们作为软件工程师所写的核心。假设我们正在开发一个计算器应用程序，我们已经有了要添加的功能。现在我们添加了一个乘法方法，我们将编写单元测试来测试新的乘法方法。

#### 开源依赖测试

开源是我们编写的许多应用程序的支柱。尽管这给我们留下了一个有趣的问题；如果我们不编写库，我们如何测试这些库，或者假设代码覆盖率支柱有一定的质量水平。通过处理库被包含和贡献的速度，一句谚语“开源像牛奶不像酒一样老化”被证明是正确的。

作为工程师，我们对自己创造的东西感到非常自豪，一旦我们对自己的特性质量感到满意，就该将特性集成到应用程序/平台的更大范围内了。集成测试的一大重点是验证和测量您对更大的应用程序的影响。

### 你造成的影响

软件很少是在真空中创建的，你的特性必须放在某个地方。测试对更广泛的应用程序或平台的影响至关重要。如果作为人类，我们是我们经历的总和，那么我们的系统就是我们多年来所有贡献的总和。

#### 集成测试

将您的特性合并和集成到文件夹中是软件开发的关键。[集成测试](https://en.wikipedia.org/wiki/Integration_testing)侧重于不同模块和环境的组合。尽管传统的测试方法可能会将集成和系统测试[例如，在环境中]区分为不同的关注点。

#### 浸泡测试

考虑到生产负载，[浸泡测试](https://en.wikipedia.org/wiki/Soak_testing)用于验证系统行为。浸泡测试与[负载测试](https://en.wikipedia.org/wiki/Load_testing)相似，在负载测试中，您将负载置于系统上，但是浸泡测试持续的时间更长。浸泡测试不同于性能测试，因为浸泡测试旨在发现容量边缘的弱点。

#### 性能试验

性能和转化率之间有直接的关联。[性能测试](https://en.wikipedia.org/wiki/Software_performance_testing)是获取系统性能并为[SLA](https://en.wikipedia.org/wiki/Service-level_agreement)做基线测试。在构建功能时，了解考虑到环境基础设施和关注点的端到端性能是未知的，直到您进入这些方面。像任何其他测试一样，有反馈和调整性能测试结果的能力。

#### 混沌工程

由于我们工作的系统的复杂性，一个被称为开发迷雾的概念出现了；类似于[的战争迷雾](https://en.wikipedia.org/wiki/Fog_of_war)，在分布式系统中很难对你的变化有情境意识。有了[混沌工程](https://harness.io/2020/03/chaos-engineering-your-continuous-delivery-pipeline-is-the-best-place-to-experiment/)，你正在注入失败来建立系统的弹性。更有甚者[在平台/系统/应用程序的某些部分注入失败](https://community.harness.io/t/gremlin-chaos-workflow-breaking-things-on-purpose/384)，在这些地方你可能认为失败是不可能的。

有了这么多的测试方法和方法论，在过去的[瀑布](https://en.wikipedia.org/wiki/Waterfall_model)日子里，等待开发完全结束来开始执行或者甚至构建测试用例可能会拖长项目时间并延迟有价值的反馈。打破开发和质量保证孤岛的一部分是接受测试驱动的开发方法。

### 测试塑造发展

打破开发和质量保证筒仓的很大一部分是测试在开发团队的 DNA 中更加根深蒂固。[测试驱动开发](https://en.wikipedia.org/wiki/Test-driven_development)，或者 TDD，关注于以测试用例为中心的需求，作为一种开发方法。如果我们在开发之前就如何测试达成一致，那么正在开发的特性应该更加符合需求。像计算机科学中的任何支柱一样，我们只是改变了复杂性。TDD 非常强调测试用例的质量,“通过测试的构建”可能会限制开发团队的回旋余地。

作为一名工程师，你可能会花很多时间构建测试用例。我早期尝试实现代码覆盖的一些挑战是由于[模仿](https://en.wikipedia.org/wiki/Mock_object)(模仿对象)。在我的方法中，创建几乎和代码行数一样多的代码来测试，这看起来很奇怪，而且在我们完成项目后，模拟会消失。尽管随着管道的出现，您可以在项目结束后很长一段时间内保持所有围绕测试的艰苦工作。

### 管道的重要性

编排您的测试/信心建立步骤是您的软件交付管道的关键部分。测试自动化供应商 Mabl 谈论 [DevTestOps](https://www.infoq.com/news/2020/05/shift-left-test-mabl-devtestops/) 接受你的测试套件作为管道的一部分的重要性。基本原理是有反馈，甚至工程师知道他们在项目上的表现有助于缩短学习曲线和提高质量。

当组织你的测试时，在创新和控制之间微调收音机转盘有时很难做对。你不想扼杀创新，但你也想确保质量、一致性和控制。在下图中，在 Harness[特别是在我们的 Harness 大学],我们宣扬一种“拧紧螺丝”的模型。当您遍历每个阶段/环境时，增加测试套件的严格性。

通过提高严格性，创新和补救可以在没有重大障碍的情况下发生。Harness 在这里与您合作，让您的测试套件，现在和未来，进入管道。

### 驾驭你的伙伴

利用 Harness 平台的好处是在软件交付中编排新的和旧的范例。随着新的测试方法的出现，例如[混沌工程](https://community.harness.io/t/gremlin-chaos-workflow-breaking-things-on-purpose/384)，你可以用 Harness 平台编排这些建立信心的步骤。

design and convection 的 Harness 平台允许您将发布策略与测试套件的结果联系起来。上述工作流甚至还受益于 Harness 的[连续验证](https://harness.io/platform/continuous-verification/)，这在生产部署期间触发了回滚。如果你还没有，请随意报名参加[线束试用](https://harness.io/try-continuous-delivery-as-a-service-for-free/)并查看我们社区新成立的[线束专家](https://community.harness.io/c/harness-experts/10)版块，了解该领域的技巧和诀窍。

干杯，

-拉维