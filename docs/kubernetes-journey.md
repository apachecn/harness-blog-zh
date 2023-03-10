# ShipTalk 播客 Kubernetes | Harness 之前、期间和之后的时间

> 原文：<https://www.harness.io/blog/kubernetes-journey>

在这一集里，我们描述了集装箱化开始流行之前的那段时间，以及圣地亚哥和他的公司从此开始的旅程。

在这一集的 ShipTalk 中，我们邀请到了圣地亚哥·坎普扎诺。Santiago 是 GumGum 的首席 DevOps 工程师，他已经见识了分布式系统。Santiago 曾经为金融部门构建分布式 Java/JEE 应用程序，并在利用 Kubernetes 之前，经历了利用 Apache Mesos 和 Apache Marathon 等技术的早期容器化。在这一集里，我们描述了集装箱化开始流行之前的时间，以及圣地亚哥和他的公司从此开始的旅程。圣地亚哥[也发表了一篇出色的博客，描述了](https://medium.com/gumgum-tech/implementing-kubernetes-the-hidden-part-of-the-iceberg-part-1-76c3e9684d49)在大规模实施 K8s 时的顾虑和不同观点。

## 副本

拉维·拉赫曼 00:06
大家好，欢迎回到下一集的《船语》。这是我们{无脚本}后的第一集。我很荣幸今天能和圣地亚哥交谈。圣地亚哥，对于那些不知道你是谁的听众，也许能告诉我们一些关于你自己的事情，你在哪里工作？

**Santiago Campuzano**00:21
首先，非常感谢 Ravi 邀请我来到这里。我叫圣地亚哥·坎普扎诺。我是 GumGum 的首席开发工程师。所以，GumGum 是一家计算机视觉广告技术公司，总部设在加利福尼亚州圣莫尼卡。嗯，作为一家公司，我们已经存在了将近 12 年。我在 GumGum 工作快三年了。是的，这真的很令人兴奋。能在这里谈论我与 Kubernetes 和集装箱的经历真的很令人兴奋，你知道，所有的基础设施和所有的技术最终导致了 Kubernetes 和我们现在生活的集装箱爆炸。再次感谢你邀请我来这里，拉维。

拉维·拉赫曼 01:07
是的，当然。我很高兴能和圣地亚哥交谈。他实际上写了一篇非常好的博文，我们会链接到，他实际上讲了一些他早期的经历，我就像，啊哈！圣地亚哥目睹了整个进化过程。因为很多时候当我们谈论 Kubernetes 的时候，我们是如此关注它。但特别是像圣地亚哥这样有丰富经验的人，你会看到有些不同的事情是相同的，对吧，所以就像没有太多或演变没有那么惊天动地，就像你刚刚开始一样。所以让我们开始一段小小的旅程。让我们回到 2000 年代时光倒流机。所以让我们在 Linux 容器流行之前，对吧。这些就像是 2010 年代。但是，在播客开始之前，圣地亚哥告诉我，他还记得架设、堆叠和运行网络线路的日子，让我们不要回到那么远。但是我们可以说，你知道吗，让我们谈谈 2010 年。在你的世界里，技术前景是什么样的？

好的，是的，我以前是，我的意思是，我以前是一名顾问。对于哥伦比亚的许多公司来说，我特别关注中间件软件，比如 Java 中间件。所以我记得和 Oracle WebLogic 一起工作。甚至是 IBM 应用服务器。所以，是的，随着时间的推移，就像 VMware 和虚拟机这种重要的技术一样，虚拟机是一种将会整合的技术，甚至会为公司节省大量资金，从而加快新服务器和新应用程序的调配。因为在此之前，您只需等待贵公司的供应部门获得服务器并安装服务器。所以是的，时光倒流。所以我们有了 VMware。我记得当时的另一个宣传是 SOA，面向服务的架构宣传。所以我记得我实际上是一名面向服务的架构顾问。老实说，对我来说，这是一种混合，因为，你知道，应用程序集成已经存在很多年了。因此，这就像一个新的架构，试图解决许多问题，你知道，公司在集成服务时面临的问题。但是可能很多公司误解了这个概念。可能他们正试图把面向服务的架构修辞强加给公司。我认为，实际上，这是微服务的开始，因为当你开始使用面向服务的架构时，你必须考虑你的业务和应用程序，就像小功能和具有适当业务边界的功能，就像完美定义的业务边界。我认为这实际上是微服务的最早期阶段。我的意思是，如果我错了，请纠正我，但我认为从我的角度来看，我认为这就像是微服务的预览。

**拉维·拉赫曼** 04:27
太棒了，我甚至认为我们现在有关系了，因为在同一时期，我在 2010 年做了很多 JEE 的开发工作。这就像，我很幸运我对圣地亚哥有所了解，我们有非常相似的职业道路。实际上，我是从爪哇/J2EE 开始的。然后我做了很多 Mesos 的东西，然后很多 Kubernetes 的东西。非常相似的道路。所以让我们开始建立集装箱生活方式。因此，拥有一个以上节点的集群应用程序并不是什么新鲜事。对吗？这是我们在 Java 中做的很多事情，我在 Java 中做了很多多节点应用程序或分布式应用程序，或可分发或分布式应用程序。我记得每次使用 WebSphere ND 时。所以她应该有 9 份拷贝。

**Santiago Campuzano**05:23
顺便说一下，它的安装和配置非常复杂，你需要一个博士学位，你知道，来安装和正确配置 WebSphere ND。我是说，如果你想做好，

拉维·拉赫曼 05:36
是的，感觉很像。所以，在应用服务器中有很多概念，你知道，只是为了调用 web 容器。对吗？当我们说容器时，现在我们会想到 Docker 这样的 Linux 容器。但是有很多我们正在构建的分布式应用相当复杂的分布式应用。以前，我肯定你也是。但是，改变的是应用程序基础架构，或者我们如何安装、分发和部署应用程序基础架构。所以曾经有一个神秘的中间件工程师，谁知道那个人现在在哪里？他们失踪了。

他们现在正在找工作。

拉维·拉赫曼 06:16
是的。或者他们只是 DevOps 的工程师。所以，让我们来谈谈集装箱化实际上做了什么。所以你和我过去常常制造战争和罐子，然后把它交给别人，或者我们可能再次成为那个人，我们把它交给自己，然后用它来部署东西。但是让我们来讨论一下，就像，把一些东西倒进一个容器里，你认为有什么好处吗？

Santiago Campuzano 06:48
我认为将应用程序转移到容器中工作有很多好处，或者像微服务一样，不管你想怎么称呼它，实际上，我记得，就像我工作的第一个项目，我的意思是，我曾经为一家非常大的哥伦比亚公司工作，比如一家保险公司。这家公司的核心应用程序非常庞大，完全是用 Java 和 PL/SQL 编写的。所以他们想把这个应用分成小块，比如说微服务。我记得我开始做这个项目的时候，就像是一个开发工程师。所以在那个时候，我们想实际上使用 Docker，Docker 就像，在其最早的阶段。因为在那个时候，你知道，Mesos 和 Marathon 也喜欢它的早期阶段，它不像是一个成熟的产品。但是，就像，我们看到的使用容器的主要好处是，嗯，主要是资源分配，你知道，资源隔离，但然后是特定的应用程序，因为在那个时候，如果你有，你知道，10 个 Java 应用程序在同一个虚拟机上运行，它们会相互竞争资源，我的意思是，主要是争夺 CPU，因为在某些时候，你可以隔离内存，你知道，设置 Xmx， 和 Xms，但它们不会，它们会相互竞争 CPU、网络和 I/O。这是我们从中获得的第一个好处，比如将资源相互隔离。 我们获得的另一个好处是能够纵向扩展微服务的不同部分，例如，如果您的应用程序的消息传递部分出现问题，您可以纵向扩展这些微服务，而不是纵向扩展整个整体。因为正如我刚才提到的，该保险公司的核心应用程序就像一个巨大的庞然大物。你知道，实际上，我记得这场战争就像一个十亿字节，甚至超过一个十亿字节，所以它就像一个巨大的庞然大物。因此，实际启动该应用程序通常需要 15-17 分钟，因为他就像一个完整的整体，启动并连接到数百个组件、后端数据库，之后，我们将这个整体分解为大约 12 或 15 个不同的微服务。很明显，这些微服务的启动时间，而不是几分钟。现在他们是第二。正因为如此，很明显，他们可以让团队在每个微服务上单独工作。因此，你知道，不是让 100 名开发人员在 monolith 上工作，你可能会有小团队或六七名开发人员专注于单个微服务，显然，这也有挑战，显然，实施或破坏 monolith 会有缺点。不过，我们可以以后再讨论。所以，对我来说，这是开始使用微服务或容器的最大好处。

拉维·拉赫曼 10:16
太棒了。是啊，太好了。就像，真的，我喜欢你的解释，你知道，很多时候，你知道，你实际上受到 CPU 的限制，你没有意识到这一点，因为 Java 非常尊重自己的内存，但 CPU。没错。现在我们越来越近了，我们肯定会继续朝着库伯内特斯前进。对吗？所以我们快到了。所以慢慢地。所以现在一只脚一只脚地离开 JEE。因此，当我们部署时，比如说，部署到 ND 或某种集群部署，这是非常标准的，对吗？就像，我们知道如何负载平衡，对吗？因此，我们的应用程序可能有八个节点，但你知道，我们在这之前有某种软件负载平衡器，它会计算出，你知道，我们将连接到 IBM 的 Oracle 或 Red Hats，对吗？就像他们的，他们特殊的路由机制，但是现在我们有了容器，所以我们可能不再使用应用服务器了。因此，我们喜欢的一些东西，你知道，如果你只有几个容器，你就要自己重新布线，对吗？你自己在使用右，Apache Mod-JK 或其他什么，现在这是我们要开始介绍的。另一个概念是集装箱蔓延。对吗？因此，如果您认为虚拟机蔓延是不好的，那么很容易旋转容器，并且它们也会死亡。但是让我们来讨论一下为什么要有一个容器编排器，好的，让我们开始吧。我正在带领 Santiago 第一次体验 Apache Mesos 和 Apache Marathon，Kubernetes 的前身是这两个作业调度程序项目，实际上，后来它成为了 Mesosphere 产品。但是为什么不说说通往梅索斯的路呢？或者为什么需要它？

**Santiago Campuzano**12:08
好的，很明显，正如我刚才提到的，在我们打破这个庞大的整体后，我们管理着 13 到 15 个微服务，很明显，这给我们带来了一些挑战，例如，如果你旋转一个 Docker 容器，这个 Docker 容器将会显示一个特定的端口，因为在容器内，你会有端口 80，对，HTTP 端口。但是，如果您想向您的主机公开该端口，您知道，这可能是一个随机端口。因为如果你想旋转 10 个容器，对于同一个微服务，很明显，你不能暴露同一个端口。因此，您将有随机的端口暴露给主机。这是第一个挑战，你知道，负载平衡器或任何资源如何对传入的请求进行负载平衡，它们如何知道正在运行的容器，以及这些容器上有哪些端口，对吗？因为很明显，使用容器的目的是为了改变负载。所以很明显，你会扩大和缩小你的港口，或者，对不起，你的集装箱。因为你有不同的机器或不同的服务器，所以你不知道这些新容器会在哪里，你知道，旋转起来，或者你可能知道，但你不想控制它。所以实际上，回到那些日子，甚至在做那件事之前，我记得我写了一个 shell 脚本，实际上，来管理它。但是维护外壳脚本非常困难，因为在外壳脚本中，我硬编码了容器的名称，例如我必须静态定义每个容器的暴露端口，例如特定微服务的最小和最大容器数量。所以就像超级超级手动。实际上，shell 脚本以某种方式工作，你知道 shell 是什么，甚至可以与我们的负载平衡器进行交互，我想如果我没记错的话，它就像一个 Cisco 负载平衡器。这个叫做负载平衡器的工具能够连接和分离容器，但这都是 shell 脚本的魔力。所以维护起来并不容易。所以最早的舞台上就出现了梅索斯和马拉松。因此，很明显，Mesos 和 Marathon 是试图解决这个问题的解决方案，你知道，如何编排容器，如何调度容器，如何为这些容器正确分配资源，如何了解单个节点中整个集群的可用 CPU 和内存量。你知道，所以这是一个很好的解决方案。你知道，为了我们所面临的斗争。但是很明显还有其他问题没有被 Mesos 和马拉松解决，比如安全，比如日志，比如监控。比如，还有什么服务发现？所以像 Mesos 和 Marathon 一样，它们涵盖了日程安排的基本问题。但是你知道，使用 coordinate 处理微服务和容器，这不是你唯一的问题，你有更多的问题，不仅仅是调度问题。这是引用的，就像之前的，或者说是 Kubernetes 的前身，所以是的，实际上，我们在信使营销方面的经验真的很短。它持续了一段时间，实际上，我离开了那家公司，就在我实施了这个微服务架构、Docker、Mesos 和 Marathon 之后。但是，是的，这是我的经验，因为它是一个模型。老实说，我还挺喜欢的。因为它是一个开源工具。这是非常非常好的维护非常好的设计。但是，是的，很明显，它缺少了很多东西。

拉维·拉赫曼 16:15
的确如此。我真的很喜欢那段旅程，你知道，很多人不知道那种挣扎，对吧。但是当集装箱化的时候。你说的每一件事都是正确的。就像你需要一个管弦乐队因为时间安排，位置安排。甚至就连你的容器也会像死了一样死在一个 WebSphere 节点上。但你知道，他们会在几个人的帮助下回来，但容器会一直死去。对，你再把它们放回去。所以让我们快进吧。所以我想观众们，你知道，他们可能熟悉老歌 k8，Kubernetes。但是让我们来谈谈你的博客文章。所以圣地亚哥真正给我留下深刻印象的是，他实际上是在谈论引用博客，这是冰山的隐藏部分。很多你在 Kubernetes 上没有想到的事情。所以 Kubernetes 现在几乎无处不在。就像我认为大多数人，你知道，至少听说过它。但我现在会利用你的专业知识。那么告诉我，有哪些事情只是冰山一角，对吗，比如你知道的一些问题，你不得不解决，这些问题或多或少是你在博文中提到的住房问题？

**Santiago Campuzano**17:33
所以实际上，写那篇博文的想法对我来说是一种启示。但是我的意思是，我已经在 GumGum 工作了，就像我刚才说的，最初是三年。在这三年中，我一直致力于 Kubernetes 的实现。因此，在 GumGum 工作之前，其他公司可能也会尝试实施 Kubernetes，但在 GumGum 这里就像我第一次认真实施 Kubernetes 的生产级产品。所以，我的意思是，库伯内特是惊人的。我们会说我会从这个开始。但是大多数人都忽略了 Kubernetes 的很多方面。我的意思是，就像，冰山的一角就像那些关于 Kubernetes 的惊人的事情。对，比如服务发现，比如容器编排，比如资源管理，对吗？这只是冰山一角，因为这些是将 Kubernetes 卖给大多数开发者的东西，对吧。所以这将是一个写一次就可以在任何地方运行的想法。这是大多数开发者会为 Kubernetes 购买的想法。但是，我说，这是一座冰山，因为，你知道，在表面之下，有许多挑战，许多问题，当你开始实施 Kubernetes 时，你不得不真正遭受。对于像 GumGum 这样的企业来说。我的意思是，GumGum 不是一个大公司，是一个中等水平的公司。但是现在，我们大概有 30 个 Kubernetes 集群在运行生产，可能还有一堆应用程序。是的，这就是我写这篇博文的想法，尽可能详细地描述我们在实施 Kubernetes 时面临的所有挑战和问题，以及我们如何解决这些问题。我是说，我们如何解决这些问题。我的意思是，我不是说这是解决这些问题的唯一方法。但这是我们的方法，你知道，解决所有这些差距或问题或限制，正如我提到的，Kubernetes 没有我的意思是，不包括一些电池，正如我在文章中所说的。你必须提供一些电池。对 Kubernetes 来说，比如日志记录、监控、安全、卷管理。所以，是的，实际上，这就是文章的全部内容。我正在准备文章的第二部分，因为这篇文章够长了。所以我会在第二部分提到冰山隐藏部分的其他方面。

拉维·拉赫曼 20:23
太棒了。我对第二部分感到兴奋，我认为有一件事，比如说，人们使用他们桌面上的 MiniKube，你知道，他们没有预料到 Kubernetes 是多么可插拔。所以，就像，你浏览文章说你正在改变某些供应商，或者你正在改变 Kubernetes 上的某些观点。这真的很难，对吧？如果你喜欢的区别，我认为你的方法你的软件工程师，对，所以喜欢你开始作为一个软件工程师，我也是；我认为，如果一个人是从系统工程师开始的，那么组织中的一些紧张关系就会出现，所以如果你还记得那些 runbooks，比如 IBM 红皮书，就像，这正是你做事情的方式。对吗？是啊，他们已经习惯了。但是作为一名软件工程师，就像你和我一样，我们习惯于一遍又一遍地尝试，直到我们做对为止。所以 Kubernetes，这是一个尴尬的桥梁，你知道，它是一个基础设施，作为软件工程师，首先，你知道，我们可以改变事情。不要担心，如果你不喜欢它，我们会重新塞，我们现在会用 Istio，而不是印花棉布，或其他东西，只是在那里做一些东西。但是作为系统工程师，他们不喜欢这样。他们说，我们需要知道最佳实践。你说得很有说服力，很多 Kubernetes 是一种新兴的做法。对吗？因此，最佳实践并不存在。这只是冰山一角。所以我想在播客中总结两个问题。但是等等，你认为生态系统会走向何方？就像你离它很近一样。比如，如果你有一根魔杖，你会说在整个 Kubernetes 生态系统中哪里有最大的改进空间？

圣地亚哥·坎普萨诺 22:07
我想是的。所以就像你刚才说的，Kubernetes 生态系统是巨大的。Kubernetes 架构的特点是，该架构是可插拔的。因此，你可以插入许多组件，如用于网络的 CNI 插件，如 DNS 插件，如入口控制器，所以 Kubernetes 是超级可插拔的，生态系统是巨大的。事实上，我在文章中提到过，如果你去 CNCF 的 Kubernetes 景观，它是势不可挡的，你知道，在某些时候，所以如果你试图查找入口控制器，你可能会找到 20 或 30 个不同的入口控制器。所以你会想，伙计，什么才是正确的？我的意思是，我应该使用什么，或者您尝试查找卷管理提供商，可能会有，我不知道，10 或 20 个不同的卷管理提供商。所以我认为可能在短期内，你知道，这种情况可能会变得稳定，在某个时候会变得更加稳定。我认为一些产品，或者一些 Kubernetes 的供应商将会更加成熟，将会被更多地使用，可能还有一些其他的，你知道，因为现在，我们正生活在炒作之中，我想说可能很多人都在试图，你知道，很多公司，很多公司和供应商都在试图为 Kubernetes 销售产品。因此，炒作并没有让这个景观变得越来越大。但我认为这可能会解决。很可能我们会有更稳定的产品和供应商。显然，这意味着您将有多种选择，但您可以在 Kubernetes 中实施的选择会更少，而且会更成熟，因为我记得曾与 GumGum 的一位同事合作过，她想要实施，就像网络提供商的测试版，而且是针对生产 Kubernetes 集群。我当时想，不，我是说，这是个不错的产品，但还不够成熟。你知道，它是在它是在一个阿尔法或贝塔版本。事实上，我认为这个项目现在正因为这个原因而被否决，因为它刚刚开始，所以我认为这将发生在 Kubernetes 生态系统中。你知道的很多公司现在都试图从 Kubernetes 上赚钱。每个人都试图为 Kubernetes 出售任何东西。

Ravi lach man24:43
我们应该为你的车做一个 Kubernetes 空气清新剂。

Santiago Campuzano 24:47
对，这实际上会卖出数百万部。

拉维·拉赫曼 24:56
是的。是啊，很棒的回答。我的意思是，这和任何答案一样有说服力，这是来自经验的答案。就像其他技术一样，对吗？就像任何快速发展的技术一样，成熟，我们称之为来自像圣地亚哥这样经验丰富的建筑师，你已经看到了来自 Java 世界、容器世界、Kubernetes 世界的多次浪潮。所以我真的，真的很喜欢我们的谈话。我总是以一个问题结束播客。这是我们播客的最后一个问题。这是一个内在的问题。所以一个哲学问题。比如说，你走在街上，你今天住的地方，你遇到了一个年轻的圣地亚哥，他刚刚从大学或学校毕业，你会对年轻的自己说些什么，可能是任何事情，比如，不要去坐牢，不要吃那个，你知道，就像，这可能是任何一条建议，他会告诉你年轻的自己？

**Santiago Campuzano**25:52
我会说 Santiago，不要学习计算机科学，请学习哲学或其他不同的东西。我只是在开玩笑。我只是在开玩笑。大概吧。我没有对年轻时的自己说。是的，多一点，多一点怀疑。多点耐心。可能更多，我不知道。享受你的职业生涯。你在正确的道路上。继续这样。

拉维·拉赫曼 26:23
给你，伙计。

圣地亚哥·坎普萨诺我真的真的热爱我的职业。老实说，我真的热爱我的职业，我的事业，我很幸运。事实上，我将在本期播客中揭示这一点。但是当我还是一名大学计算机工程师学生时，我的梦想是为一家非常大的美国公司工作。这个梦想实现了。我是一名首席调试工程师。我从未想象过管理一个团队。我现在正在做这件事。所以，非常感谢 Ravi 邀请我参加你的播客。事实上，我必须承认这是我第一次用英语播客，因为英语不是我的第一语言。所以，非常感谢。我以为会有更多的狭窄，但不是这个。这

拉维·拉赫曼非常棒。你英语说得比我好。而且我只懂英语。好了，非常感谢你，圣地亚哥，感谢你抽出时间参加播客。我确实喜欢它。听众会觉得这很棒。是的，再一次，圣地亚哥。非常感谢你来到 ShipTalk

圣地亚哥·坎普萨诺 27:40
非常感谢拉维。再次，伙计们，无论谁在听这个播客，请尝试利用；顺带一提马具很神奇。