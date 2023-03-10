# 如何构建线束仪表板|线束

> 原文：<https://www.harness.io/blog/how-to-build-harness-dashboards>

下面深入介绍如何创建您自己的定制仪表板。

在我们的[上一篇文章](https://harness.io/blog/harness-dashboards/)中，我们介绍了 Harness Dashboards，这是我们新的定制仪表板解决方案，有助于通知运营、识别瓶颈和推动业务成果。我们强调了几个跨各种 Harness 模块的现成仪表板的例子，这些仪表板使得跨组织的团队能够分析和测量软件交付，并消除猜测。在本帖中，我们将讨论如何定制仪表板，以使各种利益相关者更加专注和高效。

## 概观

仪表板使您能够使用对您最重要和最相关的指标构建和添加自定义图块。Tiles 可以从不同的线束模块中查询数据并进行可视化。您可以向仪表板添加任意数量的图块，四处移动图块，并配置布局以增强数据流——还可以添加文本图块以获得额外的上下文和元数据。

利用仪表板可以配置全局仪表板级别的过滤器，以快速切换上下文。仪表板打包了高级报告功能，使您能够随时了解最新数据。还有警报功能，可以在事情看起来不太对劲时通知您。

## 用户定义的仪表板

在构建仪表板时，您可以利用 Harness 的现成仪表板作为模板，通过克隆仪表板并根据需求进行增量更改来快速开始。或者，您可以从头开始构建仪表板。

自定义用户定义的控制面板支持透明和数据驱动的决策。这种灵活性提供了一种简单而有效的方式来可视化可操作的见解并将反馈导入流程，使最终用户能够创建特定于角色的视图，而不是一种一刀切的解决方案。创建自定义视图是一个简单的三步过程:

*   创造
*   安装ˌ使成形
*   合作

### 创建仪表板

*   在线束中，导航至仪表板。
*   在仪表板中，单击+仪表板按钮。
*   选择名称、文件夹，还可以选择添加标签。

### 配置仪表板

创建仪表板后，下一步是向仪表板添加图块和文本。当您向仪表板添加图块时，它们会自动调整大小并放置在仪表板的底部，但是您可以移动和调整图块的大小以保持数据的逻辑流动。您还可以在创建切片后对其进行编辑，以调整切片、可视化效果或基础查询的名称。

*   编辑仪表板。
*   单击仪表板窗格左上角的添加图块，然后选择可视化。
*   您将看到 Harness 在所有模块中公开的各种数据模型:CI(交付和测试度量)、CD 和特性标志(交付度量)以及 CCM(业务影响)。
*   浏览是查询的起点，旨在探索特定的主题领域。选择感兴趣的探索并继续。
*   命名切片，选择要可视化的字段，添加过滤器以确定数据范围，从大量可视化选项中进行选择，然后点击运行以立即获取结果。
*   开心的时候就存！

仪表板可以包含来自不同数据模型(CI、CD、FF 和 CCM)的数据。Harness 提供了一个单一平台，可以在一个仪表板中看到整个软件交付生命周期。

完成的仪表板可能如下所示:

### 在仪表板上协作

仪表板可以导出为 PDF 和 Excel 格式，以便在其他系统中共享和处理。它们还带有:

定制仪表板不受所公开的一级字段列表的限制——它们支持广泛的定制功能。第一类字段和这些函数一起，可用于为特定用例创建定制维度，为用户提供极大的灵活性。

## 结论

您可以在我们的[文档](https://ngdocs.harness.io/category/id0hnxv6sg-dashboards-custom)中了解更多关于 Harness 仪表盘特性和功能的完整列表。

还有问题吗？[联系我们](mailto:support@harness.io) -我们很乐意帮忙！