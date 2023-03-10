# 线束 API 测试方法|线束

> 原文：<https://www.harness.io/blog/harness-api-testing-methodology>

在这篇博客中，我们将分享我们的方法，作为其他软件公司在优先考虑 API 安全测试时可以考虑的有用参考。

随着网络安全攻击的不断增加，对于任何组织来说，拥有一种安全测试方法来保护其 API 比以往任何时候都更加重要。保护 API 有多种方法，Harness 开发了一种独特的方法。在这篇博客中，我们将分享我们的方法，作为其他软件公司在优先考虑 API 安全测试时可以考虑的有用参考。

## 什么是 API？

应用程序编程接口(API)是允许两个应用程序相互通信的软件中介。[根据 Gartner](https://www.gartner.com/en/information-technology/glossary/application-programming-interface) :

> 应用程序编程接口(API)是提供对应用程序或数据库中的服务功能和数据的编程访问的接口。它可以用作开发与人类、其他应用程序或智能设备的新交互的构建块。公司使用 API 来满足数字化转型或生态系统的需求，并启动平台商业模式。

每次我们使用任何应用程序——无论是发布到脸书，发送文本或 Slack 消息，还是在手机上查看天气——我们都在使用 API。举个例子:当你在手机上使用一个应用程序时，这个应用程序连接到互联网，并向指定的服务器发送数据。然后，服务器检索该数据，对其进行解释，执行必要的操作，并将其发送回您的手机。然后，应用程序解释这些数据，并以可读的方式向您提供您想要的信息。所有这些都是通过 API 实现的。

像 [OpenAPI](https://swagger.io/specification/) 或 [swagger](https://swagger.io/specification/) 这样的规范有助于定义描述 API 所需的文件。这些文件然后帮助组织识别必要的文档、集成和测试工具，以有效地管理他们的 API。

## 什么是 API 安全测试？

API 安全测试包括漏洞测试，以防止攻击并降低组织的风险。虽然知道 API 是密封的很好，但您也希望主动发现这个过程中的任何安全漏洞，以便工程师可以在它们影响客户或业务之前修复它们。此外，这种测试有助于确保 API 忠于其定义的规范。

安全测试有助于确保满足基本的安全要求，包括用户访问、加密和身份验证等条件。API 扫描背后的想法是精心制作输入，以诱使 API 出现错误和未定义的行为，本质上是模仿潜在黑客的行为和攻击媒介。

以下是安全性测试 API 所必需的高级步骤:

1.  定义需要测试的 API。
2.  测试人员使用各种规范格式，包括 OpenAPI v2 / v3、Postman 集合和 HAR 文件，提供关于 API 输入和输出的信息。
3.  API 安全测试使用这些信息来构造适合 API 期望的输入的模糊输入。
4.  API 安全测试的输出是在[模糊化 API](https://research.aimultiple.com/api-fuzz-testing/) 时发现的任何漏洞或错误的报告。这可能包括 SQL 和操作系统命令注入、授权/认证绕过、路径遍历问题，以及开放 Web 应用安全项目([OWASP)10 大 API 漏洞](https://owasp.org/www-project-api-security/)，包括身份验证失败、安全配置错误和数据泄露。

虽然许多组织都有团队和部门致力于生产后的测试，但我们越来越多地看到 API 安全测试正在成为 DevOps 管道的一部分。这是有意义的，因为它确保在代码投入生产之前发现漏洞。

## 为什么现在要进行 API 测试？

作为所有行业现代软件开发的基础部分，API 的数量持续增长。API 使用量的增加部分是由于组织为促进 API 的采用而开发的标准。因为 API 是许多应用程序的核心，所以在软件开发生命周期(SDLC)中采用安全性测试比以往任何时候都更重要。

确保 API 符合已发布的规范，并能抵御潜在的恶意输入，对于组织的整体安全性至关重要。根据 Salt Labs 的 [Q1 2022 年 API 安全状况报告](https://salt.security/blog/companies-are-struggling-against-a-681-increase-in-api-attacks-the-latest-state-of-api-security-report-shows)(2022 年 3 月发布)，在过去的 12 个月中，API 攻击使 API 流量的增长翻了一番多。该报告还指出:

*   [95%运行生产 API 的组织](https://salt.security/blog/companies-are-struggling-against-a-681-increase-in-api-attacks-the-latest-state-of-api-security-report-shows)在过去 12 个月中经历过 API 安全事故
*   大多数组织没有准备好应对这些挑战，超过三分之一的组织(34%)没有 API 安全策略
*   传统的安全措施[继续失效](https://salt.security/blog/companies-are-struggling-against-a-681-increase-in-api-attacks-the-latest-state-of-api-security-report-shows)，给组织一种虚假的安全感

## 线束 API 测试策略

虽然 OWASP 十大 API 漏洞非常关键，但要真正将您的开发运维提升到一个新的水平，这个列表实际上只是一个起点。Harness 遵循 API 安全测试的完整生命周期，将安全性和 DevOps 一起带入 DevSecOps。

测试不是一次性的项目。为了使您的 API 免受漏洞的影响，这是一个需要定期重复的持续过程。在 Harness，我们使用我们的[安全测试编排](https://harness.io/products/security-testing-orchestration) (STO)模块来测试[自动化](https://harness.io/blog/product-updates/sto-key-capabilities/)和编排。使用 STO，我们定期运行直接从管道触发的扫描，并在扫描结果包含严重或高度漏洞时发送电子邮件。然后，我们可以不断完善触发扫描和警报的标准。

我们的测试策略涵盖五个关键领域:

1.  界定和理解 API 和规范
2.  映射攻击
3.  自动化和手动测试(OWASP API Top 10)
4.  可交付成果
5.  自动化和扩展

### **1。范围界定&了解 API 和规范**

**定义范围**

重要的是首先定义我们将覆盖的所有领域作为测试的一部分。通常，组织使用 swagger 或 OpenAPI 规范来记录他们的所有 API，并且可以利用这些来理解范围。

**了解 API 和业务用途**

为了确定安全漏洞对业务的影响程度，理解 API 及其业务用途至关重要。此外，这有助于我们构建针对 API 的定制攻击。

API 扩展了业务可以提供的能力和功能，而无需在集成后投入大量资源。为了充分利用 API，企业通常使用 API 来:

*   与第三方 API 集成
*   构建供内部使用的 API
*   构建 API 并公开 API 供外部使用

理解当前测试属于哪一类是关键。像攻击者一样思考很重要。

**首先，检查作为合同的规范-API**

API 本质上是客户机和服务器之间或者两个应用程序之间的契约。在开始任何实现测试之前，确保契约正确是很重要的。这可以首先通过检查规范(或服务契约本身，例如 Swagger 接口或 OpenAPI 引用)来完成，并确保端点正确命名，资源及其类型正确反映对象模型，没有缺失的功能或重复的功能，并且资源之间的关系正确反映在 API 中。

### 2.映射攻击

**思维导图攻击**

既然您已经知道了 API 的设计目的、它们的底层技术和规范，那么思考攻击就容易多了。

一般来说，所有容易摘到的果子都会被自动化工具覆盖。这里您真正想要关注的是如何覆盖业务逻辑流。关注特定于业务的流程，尝试找到任何自动化安全工具都很难找到的场景。

你也可以在这里关注链式攻击。将报告的工具作为基线，并将它们与其他发现关联起来，以创建攻击场景，这可能是本文的重点。

### 3.自动化+手动测试–OWASP API 前 10 名

**回顾 OWASP API 前 10 名**

OWASP 基金会列出了 API 的十大安全威胁。查看他们网站上的列表，让您的团队做好准备。这是任何类型的安全测试的基础。

**运行自动化工具**

有许多自动化工具可以帮助提高效率。这些自动化工具将节省时间和资源，而不是依赖手工测试。我们在下面分享了一些我们最喜欢的:

*   BurpSuite Pro 和 [Traceable AI](https://app.traceable.ai/api-dashboard?time=1h) 有助于发现安全问题，还有许多其他支持工具
*   像[邮递员](https://www.postman.com/)和/或 [SoapUI](https://www.soapui.org/downloads/soapui/) 这样的开源工具
*   Burp 有一套广泛的支持插件，可以用来关注各种攻击，比如 [OpenAPI 解析器](https://portswigger.net/bappstore/6bf7574b632847faaaa4eb5e42f1757c)

**测试业务逻辑流程**

业务逻辑漏洞是 API 的设计和实现中的缺陷，使得攻击者能够引发意外的行为。这可能使攻击者能够操纵合法功能来实现恶意目标。

例如，查看如何将特定权限授予资源，如何验证许可，以及如何计算客户成本。如果上述场景中存在潜在的操纵或缺陷，那么它就是机密性、完整性和可用性，也称为 CIA 违规，这可能导致企业收入损失。

### 4.可交付成果

报告我们在测试过程中迄今为止的发现是最终的结果。为了让风险承担者意识到风险，在 JIRA 或任何其他票据系统中创建相关联的任务，并在单个安全仪表板上跟踪它们。

### 5.自动化和扩展

考虑到全年快速开发的数量，安全团队必须跟上软件交付的速度。自动化使规模成为可能。

在每个版本中，有各种各样的方法来自动化 API 测试和测试变更。因为不可能在每个发布周期测试所有的 API，你需要选择一个节奏来执行完整的 API 测试。对于其余的版本，您将只选择增量。

API 测试在我们的管道中的集成将我们的 DevOps 带到了一个新的高度，实现了一个成熟的 DevSecOps 实践。

## 利用安全测试流程编排

最终，对于安全性测试来说，没有“一刀切”的方法。然而，鉴于对 API 攻击的增加，拥有合适的工具是主动保护的关键。

想了解更多关于 Harness 如何帮助自动化 API 安全测试的信息吗？[今天就申请试玩](https://harness.io/demo/)驾驭 STO！