# 引入对功能标志的内部支持，以更安全地部署|线束

> 原文：<https://www.harness.io/blog/introducing-feature-flag-on-prem-support>

这种新的部署模式对于拥有复杂的自托管软件交付模式的组织尤其重要，包括具有高度特定的监管和实施要求的政府和公共部门组织，以及企业安全公司。

我们很高兴地宣布，线束特征标志(FF)模块现可用于内部部署。这种新的部署模式对于拥有复杂的自托管软件交付模式的组织尤其重要，包括具有高度特定的监管和实施要求的政府和公共部门组织，以及企业安全公司。

这一版本加强了我们对 Harness 的关注，以构建降低风险的解决方案，并使[软件交付最佳实践](https://harness.io/blog/continuous-delivery/best-practices-software-delivery/)更容易、更安全地采用——所有这一切都不会牺牲特性标志给工程组织带来的速度。

特性标志是一种方式，开发者可以有条件地打开或关闭他们代码的某些部分。它们是一种将更改投入生产的手段，能够在以后以受控的方式打开新功能，或者以相同的方式隐藏和删除它们。 [Harness Feature Flags 模块](https://harness.io/products/feature-flags)为这些功能提供了复杂的规则、治理、用户管理、直观的 UI 等等。

以自动化和可扩展的方式确保合规性的能力是推动采用功能标志作为关键软件交付过程的关键支柱。现在，通过利用功能标志的内部部署，工程组织可以将功能管理集成到他们的软件交付流程中，并通过最少的手动工作来扩展他们的解决方案。

对 Harness 功能标志的本地支持的可用性将 Harness 与大多数不支持本地部署的 SaaS 功能标志供应商区分开来。在内部功能管理市场上，没有其他解决方案可以与 Harness 功能标志相媲美。让我们更深入地了解一下组织如何受到现有内部功能管理解决方案市场的限制，以及利用功能标志如何填补这一空白。

**在软件交付中平衡速度和风险**

对于需要内部交付模式的组织来说，为了有效地解决他们在功能管理方面的核心挑战，他们必须拥有自动化工作流、模板化发布管道、CI/CD 集成、GitOps 和深度治理等企业级功能。这些是有效地扩展组织对特性管理的使用所必需的能力，特别是当他们试图将特性管理集成为他们的软件交付模型的一个关键部分时。如果没有自动化和可重复性，很难达到组织寻求的规模水平。

现有的内部功能管理解决方案没有提供这些功能，最重要的是任何种类的自动化。对于需要内部托管的组织来说，尝试解决围绕提高速度和降低风险的各种挑战完全是手动的。

虽然一些组织在内部创建了功能管理的 DIY 解决方案，但实现规模化仍然极具挑战性，因为有太多的手动流程。如果不雇佣大量开发人员并在内部维护解决方案，需要运营和扩展内部解决方案的组织就无法实现所需的企业级功能。DIY 解决方案通常只包括基本的功能，例如定位用户的能力(事实上，这通常是第一个实现的用例！)，这通常是为一个团队或几个团队定制的。为了推动该工具在其他团队中的采用，或者添加更多的功能，组织必须投入开发资源来构建这个新的开发人员工具。这不是他们的核心任务，但需要开发和维护开销，以使其对整个组织有用。

现有的受管选项仅限于基本的功能管理功能，如布尔和多元标志、用户定位、分析、审计日志和基本安全(RBAC、单点登录)。这些功能不允许组织像 SaaS 解决方案那样最大化特性管理工具的价值。这一切都回到了可伸缩性，这需要自动化和可重复性。即使只有这一基本功能，缺乏自动化意味着该过程将永远保持手动；每次软件经历这个过程，都必须重新构建，而不是能够识别公共模式并重用实现这些模式的模板。

现有内部解决方案缺乏自动化、安全性和企业级功能，例如自动化工作流、模板化发布管道、CI/CD 集成、GitOps 和深度治理。

**大规模实施内部特性管理**

借助这一新添加的部署模型支持，Harness Feature Flags 将商业 SaaS 产品中的相同功能提供给了那些希望在本地部署模型中使用这些功能的用户。

政府、联邦政府和其他高安全性行业的组织现在有了一个解决方案，可以在功能管理之旅的所有阶段为他们提供支持，而不必在不提供所需功能的子选项之间做出选择。

下面是一些关键特性，利用特性标志可以为拥有复杂的自托管软件交付模型的组织提供独特的特性。你可以[在文档中阅读更多关于这些的](https://docs.harness.io/article/0a2u2ppp8s-getting-started-with-feature-flags)。

*   通过作为代码的[政策和 OPA](https://harness.io/blog/feature-flags/opa-feature-flags/) 实施全球治理
*   自动化特性发布管道
    ‍ *—计划并批准发布
    —构建发布模板
    —与外部工具集成并创建触发器
    —自动化治理*

*   开发者至上的体验，包括 GitOps 和 YAML
*   与 CI/CD 的全平台本机集成等等

除了这些更标准的功能之外:

*   布尔和多元标志
*   用户定位
*   标志管理仪表板
*   使用指标和客户分析
*   公共 API 和开源 SDK
*   小于 500 毫秒的客户端流更新
*   减轻停机风险的中继代理
*   审计线索
*   RBAC 和 SSO

所有这些功能使组织能够:

*   作为软件交付流程的一部分，集成和扩展功能标志，在实现软件交付现代化的同时确保法规遵从性。
*   即使在生产过程中，也能让开发人员在不破坏东西的情况下加快进度。
*   实施治理和法规遵从性，而不牺牲速度。

我们利用特性标志的重点是提供一个解决方案，帮助提高速度，降低风险，并改善开发人员的体验，所有这些都不需要在这些商业价值之间妥协或权衡。作为 Harness 平台的一部分，企业组织能够[将特性标志原生集成到 CI/CD](https://harness.io/blog/feature-flags/combining-cicd-and-feature-flags/) 中，并扩展关键软件交付流程，即使在本地托管时也是如此。

**开始使用功能标志实现控制之旅**

我们正在利用特性标志来使特性标志在软件开发团队中的使用民主化。无论是 SaaS 还是本地，我们都希望确保这一承诺惠及所有开发商。这不仅仅是给开发者新的工具和责任；它是关于创建一些易于使用的东西，并且从第一天起就可以根据公司和开发者的需求进行扩展。

如果您想了解如何在您的本地安装中部署 Harness 特性标志，[请求一个演示](https://harness.io/demo/next-gen-ff)来开始。

如果您是现有的 Harness 客户，将受益于现场功能管理，请联系您的客户成功经理。

如果你有足够的灵活性来玩我们的 SaaS 产品，你可以从注册[免费](https://app.harness.io/auth/#/signup/?module=cf)开始。