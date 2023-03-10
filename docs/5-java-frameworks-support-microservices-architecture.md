# 5 个 Java 框架支持您的微服务架构| Harness

> 原文：<https://www.harness.io/blog/5-java-frameworks-support-microservices-architecture>

与其问你需要什么专门的框架来构建一个新的微服务架构，不如问我们如何使用当前的框架来支持同样的目标。

早在 2016 年，许多人可能会认为这只是另一个令人难以忍受的流行词，但今天许多组织正在收获打破旧的整体应用程序的真正好处，并看到微服务可能带来的真正挑战。

对于处理大量技术债务的团队来说，微服务提供了一条通往乐土的道路。它们承诺带来更大的灵活性和更容易的可伸缩性。较小的代码基础更容易理解，并且有了清晰分离的服务，整体架构更加“干净”。

微服务带来了新的令人兴奋的可能性(蛋糕不是谎言)，但它们仍然不是没有挑战。任何告诉你不是这样的人都大错特错了(或者，更有可能的是，试图向你推销某种东西)。更高频率的发布和开发人员与运营人员之间更多的合作令人兴奋，但保持勤奋也很重要。

微服务可能被认为是构建应用程序的一种革命性方法，但这种新方法并不要求我们完全从头开始。与其问你需要什么专门的框架来构建一个新的微服务架构，不如问我们如何使用当前的框架来支持同样的目标。

但首先…简单回顾一下什么是微服务以及它们的来源:

## 微服务——简略的非历史

早在 2014 年，马丁·福勒和詹姆斯·刘易斯在他关于微服务的第一篇文章中就试图定义这种新架构:

“微服务架构风格是一种将单个应用程序开发为一套小型服务的方法，每个应用程序都在自己的进程中运行，并通过轻量级机制(通常是 HTTP 资源 API)进行通信。这些服务是围绕业务能力构建的，可由全自动部署机制独立部署”。

当时，微服务和容器化应用程序的概念是如此之新，以至于没有真正专业的工具或框架来支持构建、部署和运行这些类型的应用程序。更确切地说，焦点是调整当前的工具以用于这种新的架构风格。

在过去的五年中，该行业爆发了专门为支持新的微服务而构建的技术。但这并不意味着它们最适合每个人的需求。事实上，与 monoliths 不同，monoliths 通常是在考虑技术堆栈的情况下开发的，微服务架构中的每个服务都可以使用基于其自身功能的不同框架来构建。

这篇文章不是关于微服务的利弊，而是着眼于最适合支持它的底层技术。如果你想深入了解微服务的一些常见陷阱(当然，还有如何克服它们)，可以看看这篇文章，它涵盖了与微服务相关的主要挑战。相反，我们将回顾一些最流行的构建微服务的框架——包括传统的和容器专用的。

## 1.用于微服务的 Jakarta EE / Java EE

构建应用程序的经典 Java EE，现在是 Jakarta EE (JEE)，是面向 monoliths 的。传统上，用 Java EE 构建的企业应用程序会被打包到一个 EAR(企业归档)部署单元中，其中包括 WAR (Web 归档)模块和 jar(Java 归档)文件。

虽然没有任何技术限制排除微服务架构使用 JEE，但有一个巨大的开销成本。每个服务都需要打包成一个独立的单元，这意味着它应该部署在自己单独的 JEE 服务器中。这可能意味着部署数十甚至数百台应用服务器来支持典型的企业应用程序。

幸运的是，社区很早就注意到标准 JEE 没有解决微服务引入的新构建挑战。自 2016 年以来，许多额外的开源项目已经开始支持在 JEE 建立的微服务。

Eclipse MicroProfile 是一组基于 JEE 技术的不断发展的 API。这是一个用于构建企业 Java 微服务的 OS 社区规范，由业界一些最大的公司提供支持，包括 Oracle、Red Hat 和 IBM。

一句话:没有理由不能将 Java EE 用于微服务，但是它不能解决运行多个个性化服务的操作问题。对于那些想要将现有的 monolith JEE 应用程序迁移到微服务的人来说，有很多基于 JEE 技术的“附加”工具可以满足他们的需求。

## 2.春天(Spring Boot 和春天的云)

Spring 是构建 Java 应用程序最流行的框架之一，和 Java/Jakarta EE 一样，它也可以用来构建微服务。正如他们所说，“[微服务]在流程级别做 Spring 一直在组件级别做的事情。”

尽管如此，在 Spring 框架上启动并运行一个具有微服务架构的应用程序并不是一个最简单的过程……你需要使用 Spring Cloud(充分利用 Spring Boot)、几个网飞 OSS 项目，最后还需要一些 Spring“配置魔法”。

要深入了解如何使用 Spring 构建微服务，请直接查看这篇文章的源代码。

一句话:Spring 为微服务的开发做了很好的定位，同时围绕外部开源项目提供解决运营角度的服务。但这并不意味着这很容易。

## 3.拉贡(光弯)

光弯为我们提供了另一种选择。继续相同的主题，Lagom 用 Play 和 Akka 包装 Lightbend 堆栈，以提供一种更简单的方法来构建微服务。他们的重点不仅是为那些转向微服务的人提供一个简单的解决方案，而且要确保这些微服务易于扩展和反应。

在 2015 年接受 InfoQ 采访时，Lightbend 的首席技术官兼联合创始人 Jonas Bonér 说:

“大多数微服务框架都专注于简化单个微服务的构建，这是最容易的部分。Lagom 将其扩展到微服务系统、大型系统——这是困难的部分，因为我们面临的是分布式系统的复杂性。”

一句话:Lagom 采用 Lightbend 的功能，并在一个框架中利用它们，该框架专为构建可跨大型部署有效扩展的反应式微服务而设计。他们不仅关注单个微服务，还关注整个系统。

## 4.下拉向导

与我们在这篇文章中看到的其他框架不同，Dropwizard 是一个用于开发 ops 友好、高性能、RESTful web 服务的 Java 框架。一个自以为是的 Java 库集合，使得构建生产就绪的 Java 应用程序更加容易。

Dropwizard 模块允许挂接 Dropwizard 核心之外的其他项目，还有社区开发的模块可以挂接网飞尤里卡这样的项目，类似于 Spring Cloud。

一句话:由于 Dropwizard 是一个社区项目，没有像 Spring 和 Pivotal、Java EE 和 Oracle、Lagom 和 Lightbend 这样的大公司的支持，它的开发可能会更慢，但它背后有一个强大的社区，它是大公司和较小项目的首选框架。

## 5.Vertx、Spotify Apollo、Kubeless 等“微服务专用”框架

除了我们在这里提到的 4 个大玩家，还有很多其他项目值得一提，也可以用于编写微服务:

Vertx 也在 Eclipse Foundation 下，是一个用于在 JVM 上构建反应式应用程序的工具包。一些人可能会争辩说，它应该在四大会计师事务所中占有一席之地。

Spotify Apollo 是编写 Java 微服务时在 Spotify 使用的一套 Java 库。Apollo 包括 HTTP 服务器和 URI 路由系统等特性，使得实现 RESTful 服务变得很简单。

Kubeless 是一个 Kubernetes-native 无服务器框架。它是专门为部署在 Kubernetes 集群上而设计的，因此用户能够使用本地 Kubernetes API 服务器和网关。

附加框架包括 Spark，Ninja 和 Jodd，Restlet 和 Bootique.io。

一句话:Java 微服务领域非常大，值得关注的小参与者和行业巨头一样多。

## 最后的想法

无论您使用哪种框架或平台，构建微服务都不会与它们紧密耦合。这是一种思维模式和架构方法，最佳实践(一如既往)是为您的应用程序的独特需求找到最佳选项。

也就是说，成功实施微服务架构并不止于应用程序本身。围绕 it 的大部分成本来自所谓的开发运维流程、监控、CI/CD、记录更改、服务器配置以及为生产中的应用程序提供持续支持所需的更多成本。所以，尽情享受你的蛋糕吧，但别忘了在收获回报的同时保持勤奋。