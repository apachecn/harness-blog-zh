# 葡萄干从詹金斯噩梦中跑出来-每年节省 52.5 万英镑|马具

> 原文：<https://www.harness.io/blog/raisin-runs-from-jenkins-nightmare>

## **关于**

Raisin 是领先的泛欧财富管理平台，将零售客户与寻求扩大存款范围或使其多样化的金融机构联系起来。它们在整个欧洲都有英语版本，并在德国、法国、西班牙、英国、爱尔兰、荷兰和奥地利运营国家专用平台。2020 年，他们在美国推出了储蓄即服务分支机构

## 他们说，现代化……他们说，更容易，更便宜...

Raisin 将其应用程序迁移到云中，以利用 Kubernetes 等现代技术。

有道理。大家都在做。

他们的应用程序现代化的一个副作用是需要新的软件部署策略来减少微服务部署工作。

发现问题。

Raisin 创建了一个由 José Meyer 领导的中央 DevOps 团队来处理部署问题。

计划已创建。

该团队使用 Jenkins 和定制脚本为各种开发团队构建部署管道。

问题解决方案…等等。偏头痛来袭。

Jenkins 管道允许 Raisin 每个月部署 10 次，但是 DevOps 团队的 6 名新成员花费了 80%的时间让 Jenkins 保持站立。这相当于每年大约 70 万美元的薪水(假设每个团队成员每小时 70 美元)。在 Jenkins 维护、更新、插件添加和故障排除之间，团队几乎没有时间做其他事情。詹金斯太脆弱了，不能单独留下。

Jenkins 脚本非常敏感，经常会导致部署失败。

> José Meyer |首席 CI/CD 工程师| Raisin

由于 Jenkins 管道的复杂性，新应用程序的上线大约需要 2 天时间。就其本身而言，这听起来并不可怕，但考虑到入职后的大量维护工作，你会发现这是一次很大的时间浪费。

José和 DevOp 团队最初选择 Jenkins 是因为这是一个“免费”的解决方案。但是在处理完 Jenkins 噩梦之后，Jose 开始寻找更好的方法来部署软件。

尽管 Jenkins 是一个开源工具，但维护它的成本(更新、插件等。)成倍地取代了任何潜在的节约。

> José Meyer |首席 CI/CD 工程师

## **现代建筑的现代 CD 解决方案**

在何塞的寻找过程中，他发现了马具。利用 Harness，José和 DevOps 团队将软件部署责任分配给应用程序团队。应用程序团队现在管理他们自己的服务、管道和触发器。José的 6 人团队现在只花 20%的时间管理软件交付。这相当于减少了 60%的工作量，价值约为 52.5 万美元。

我们用马具画出了清晰的所有权线。我的团队拥有工作流和模板，每个应用团队管理自己的服务、管道和触发器。

> José Meyer |首席 CI/CD 工程师| Raisin

软件交付的民主化和自动化允许 Raisin 每月部署 53 次——比以前的部署速度提高了 5 倍。

剩下的唯一手动步骤是手动批准。这是设计好的。

> José Meyer |首席 CI/CD 工程师| Raisin

Harness 部署成功的消息很快在 Raisin 周围传播开来。应用团队开始排队使用 Harness 部署他们的应用程序。幸运的是，由于 Harness 的模板化和可重复使用的连接器，José的团队只需要 30 分钟就可以安装新的应用程序。

应用程序和 CI/CD 的现代化可能是一项挑战。也许这是一个你正准备去经历的挑战。看看马具是如何减轻过渡的痛苦的。