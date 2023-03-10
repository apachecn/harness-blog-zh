# 利用 AWS 虚拟机管理配置项|管理

> 原文：<https://www.harness.io/blog/harness-ci-aws-vms>

测试版支持提供了操作指南！在本帖中，我们将探索 AWS 虚拟机支持的特性，并探索它们的设计和架构。

Harness CI 最近增加了对 AWS 虚拟机(VM)的测试版支持。这意味着 CI 构建可以在 Harness 平台中的 Kubernetes 集群或 AWS VM 上运行。在本帖中，我们将探索 AWS 虚拟机支持的特性，并探索它们的设计和架构。

AWS VM 特性附带了对. NET 的测试智能支持。它支持使用 Kubernetes 基础设施的 Harness CI 中已经存在的所有特性。一个主要的新增功能是支持在 Windows 操作系统上运行构建。除此之外，运行步骤还可以在主机虚拟机上执行命令。因此，AWS VM 是不适合在容器内执行的 CI 管道的默认选择。

此外，steps 可以使用 AWS VM 在管道上运行 Docker 命令。这在 Kubernetes 基础设施上是不可行的，因为它限制了对 pod 的特权访问。

## 设计

每个 CI 阶段都在一个专用的 AWS VM 上运行，该 VM 在构建执行完成后终止。与在多个构建中重用虚拟机相比，这种方法的一个主要优点是不需要清理工作空间，因为每个构建都在一个新的虚拟机上运行。

这个特性需要在一个代理虚拟机上安装 [Drone Runner AWS](https://github.com/drone-runners/drone-runner-aws) 。安装带滑道的代表的步骤可在[此处](https://github.com/harness/cie-vm-delegate)查看。运行者负责 AWS 虚拟机的生命周期管理，包括创建、删除等。此外，它处理 CI 构建运行的虚拟机上的步骤的执行。运行程序在启动时启动 HTTPs 服务器，委托代理通过端口 3000 上的 localhost 与它进行交互。

CI 构建执行包括三个阶段:初始化、步骤执行和清理。所有这些阶段都是通过委派任务发生的。

### 初始化

此阶段创建运行构建所需的资源。一旦初始化任务到达委托代理，它就调用 runner 来创建一个 VM，构建将在其上运行。

Runner 使用 AWS golang sdk 创建一个 AWS VM。作为虚拟机创建的一部分，它还会在构建虚拟机上安装一个代理，特别是 lite-engine。lite-engine 安装通过一个云初始化脚本进行，该脚本从云中下载并在虚拟机启动时启动它。Lite-engine 启动一个 HTTPs 服务器，跑步者使用它通过一个安全的通道与服务器通信。

lite-engine HTTPs 服务器使用自签名证书以及服务器和客户端证书。客户端证书位于运行者上，用于向服务器验证客户端(此处为运行者)的身份。lite-engine 上的服务器证书用于加密传输中的数据。

### 分步执行

在步骤执行阶段，步骤按照 CI 管道中定义的顺序执行。一旦执行一个步骤的任务到达委托，它就调用运行器来执行它。然后，runner 通过 HTTPs 调用 lite-engine 来执行该步骤。Lite-engine 要么直接在 VM 上作为子进程运行该步骤，要么在 docker 容器上执行它。

### 清除

清理阶段标志着 CI 阶段的完成。它删除为构建执行分配的资源。委托代理在收到清理任务时，调用运行程序，运行程序删除分配给已完成构建的 AWS VM。

## 虚拟机池

虚拟机启动可能需要几分钟，尤其是 windows 虚拟机，启动需要 6-8 分钟。如果虚拟机是作为构建执行的一部分创建的，那么由于虚拟机的启动时间，它会显著增加构建时间。

Harness 使用一种池策略来维护用户指定数量的 warm AWS 实例。热实例是预先初始化的 [Amazon 弹性计算云(Amazon EC2)](https://aws.amazon.com/ec2/) 实例，其 VM 启动已经完成。每当执行具有 CI 阶段的管道时，执行初始化任务的运行程序检查 AWS 实例是否存在于池中。如果存在，则将虚拟机从池中分离出来，并分配给 CI 阶段执行。Runner 创建一个新的 Amazon EC2 实例来维护池的大小。因此，虚拟机池确保初始化只需几秒钟就能完成，而不是几分钟。

VM 池必须定义为运行程序配置文件的一部分。它允许设置池的大小，以及虚拟机的配置，包括 AMI、实例类型、网络等。

## 结论

将 CI 与 AWS VM 结合起来，可以灵活地在 Amazon EC2 实例上运行 Linux 和 Windows 版本。我们希望这一高层次的设计概述能够让我们深入了解 Harness CI 如何与 AWS 虚拟机协同工作。

想亲眼看看吗？现在就报名参加你的[免费试用](https://app.harness.io/auth/#/signup/?module=ci)驾驭 CI 吧！