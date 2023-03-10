# 终极 JSON 库:JSON . simple vs GSON vs Jackson vs JSONP | Harness

> 原文：<https://www.harness.io/blog/ultimate-json-library-comparison>

我们运行了一个基准测试，看看四个最流行的 Java JSON 库解析不同大小的文件有多快。这个基准可以帮助你决定。

JSON 是目前公认的在服务器和 web 应用程序之间传输数据的标准。我们经常不会想到我们使用的 JSON 库，但是它们之间还是有一些区别的。

JSON 通常用于传输和解析大文件。这是在 Hadoop 或 Spark 集群中运行的数据处理应用程序中常见的场景。鉴于这些文件的大小，您可以看到不同库之间解析速度的显著差异。

小文件总是以高吞吐量作为传入请求出现，并且解析它们的速度很快，因此性能上的差异起初看起来并不是什么大问题。但是不同之处越来越多，因为在流量大的时候，您经常需要快速连续地解析大量的小文件。微服务和分布式架构经常使用 JSON 来传输这类文件，因为它是 web APIs 的事实格式。

并非所有 JSON 库的性能都一样。为您的环境选择正确的解决方案至关重要。我们运行了一个基准测试，看看四个最流行的 Java JSON 库解析不同大小的文件有多快。这个基准可以帮助你决定。

## JSON 库

JSON.simple vs GSON vs Jackson vs JSONP 对于基准测试，我们查看了四个主要的 Java JSON 库:JSON . simple、GSON、Jackson 和 JSONP。所有这些库都广泛用于 Java 环境中的 JSON 处理，并根据它们在 Github 项目中的受欢迎程度进行选择。以下是我们测试的产品:

*   [Yidong Fang 的 JSON . simple](https://github.com/fangyidong/json-simple)–JSON . simple 是一个用于编码和解码 JSON 文本的 Java 工具包。这意味着它是一个轻量级的简单的库，但仍然具有很高的性能。
*   [Google 的 GSON](https://github.com/google/gson)–GSON 是一个 Java 库，可以将 Java 对象转换成 JSON，反之亦然。它提供了完全支持 Java 泛型的额外好处，并且不需要您注释您的类。不需要添加注释会使实现更简单，如果您没有访问源代码的权限，这甚至是一个需求。
*   [FasterXML 的 Jackson 项目](https://github.com/FasterXML/jackson)–Jackson 是一组数据处理工具，以其流式 JSON 解析器和生成器库而闻名。它是为 Java 设计的，也可以处理其他非 JSON 编码。根据我们对 Github 用法的发现，它是最流行的 JSON 解析器。
*   [Oracle 的 JSONP](https://jsonp.java.net)–JSONP(JSON Processing)是一个用于 JSON 处理的 Java API，即围绕消费和生产流 JSON 文本。这是 JSR353 的开源参考实现。

## 基准:2017 年

我们对大文件和小文件的库进行了基准测试。处理不同文件大小的需求(以及性能)是不同的，需要解析这些文件的环境也是不同的。

基准测试了两个关键场景:大文件的解析速度(190 MB)和小文件的解析速度(1 KB)。大文件取自 [GitHub](https://github.com/zeMirco/sf-city-lots-json) 。这个小文件是从这里随机生成的 [JSON 生成器](http://www.json-generator.com/)。

对于大文件和小文件，我们在每个库中运行每个文件 10 次。给定大文件的大小，我们对每个库每次运行进行 10 次迭代。对于每个库，每个小文件每次运行都要迭代 10，000 次。对于小文件测试，我们没有在迭代之间将文件保留在内存中，测试是在 AWS 上的 c3.large 实例上运行的。

下面完整显示了大文件的结果，但是为了节省空间，我进一步平均了小文件的结果。要查看扩展结果，[请点击此处](https://docs.google.com/spreadsheets/d/1iOSAkqRwGGbLHRkcKSyHwpOWYdSrkuQKyUIZ6ef7N-I/edit?usp=sharing)。如果你想查看小文件或库的源代码，[到这里](https://github.com/terencetaih/aws-speed)。

## 大档成绩:2017

这里差别很大！根据运行情况，杰克逊或 JSON.simple 的交易时间最快，杰克逊在总体上超过了 JSON.simple。查看所有测试运行的平均结果，Jackson 和 JSON.simple 在大文件中遥遥领先，JSONP 远远落后于第三名，GSON 远远落后于最后一名。

让我们用百分比来表示。杰克逊是所有赛跑平均时间的冠军。从两个不同的角度看这些数字，下面是百分比结果:

这些是库速度之间的巨大差异！

外卖:这是一个照片完成，但杰克逊是你的获奖图书馆。JSON.simple 在后面一个鼻子，另外两个在后视镜里。

## 小档案成绩:2017

上表显示了每个文件 10 次运行的平均值，总平均值在底部。赢得文件数量最快的图书馆的记录是:

*   GSON–14
*   JSONP–5
*   杰克逊–1
*   JSON。简单–0

查看所有文件的所有测试运行的平均结果，GSON 在这里是赢家，JSON.simple 和 JSONP 分别占据明显的第二和第三名。

杰克逊名列倒数第二。因此，尽管 JSON.simple 不是任何单个文件中最快的，但它在总体上是第二快的。尽管 JSONP 是少数几个文件中速度最快的，但它在总量上排在第三位。

Jackson 在所有文件上非常一致，而其他三个库偶尔会比 Jackson 快得多，但在某些文件上，运行速度几乎相同，甚至稍慢。

让我们用百分比来表示这些数字，再次从两个不同的角度来看这些数字:

与大文件测试相比，这些差异较小，但仍然很明显。

要点:JSON.simple 运气不好，因为它再次输掉了一场势均力敌的比赛，但 GSON 是你的赢家。JSONP 明显排在第三，杰克逊排在最后。

## 结论:2017 年

在选择 JSON 库时，解析速度不是唯一要考虑的因素，但它是一个重要的因素。在运行这个基准测试时，我们发现在所有文件大小和所有运行中，没有一个库在解析速度上超过其他库。对大文件表现最好的库对小文件表现不好，反之亦然。

根据解析速度选择使用哪个库取决于您的环境。

*   如果您有一个经常或主要处理大型 JSON 文件的环境，那么 Jackson 就是您感兴趣的库。GSON 最纠结大文件。
*   如果您的环境主要处理大量小型 JSON 请求，比如微服务或分布式架构设置，那么 GSON 就是您感兴趣的库。杰克逊最纠结的是小文件。
*   如果您最终不得不经常处理这两种类型的文件，那么 JSON.simple 在两个测试中都以非常接近的第二名的成绩出现，这使得它成为可变环境中的一个好帮手。Jackson 和 GSON 在多种文件大小下的表现都不尽人意。

就解析速度而言，JSONP 在任何场景中都没有太多值得推荐的地方。与其他可用选项相比，它对于大文件和小文件的性能都很差。幸运的是，据报道，Java 9 正在获得原生 JSON 实现，人们可以想象这将是对参考实现的改进。

如果担心 JSON 库的解析速度，可以选择 Jackson 处理大文件，GSON 处理小文件，JSON.simple 处理两者。

## 基准:2021 年

我们再次运行相同的基准，但是现在使用最新的库，并在 Java 11 上运行测试。

这些数字看起来与我们之前运行这些基准测试时大相径庭。总的来说，性能大幅提高。

## 大档案成绩:2021

最后的基准测试杰克逊是赢家，但这一次 GSON 是迄今最快的，JSONP 紧随其后，然后是杰克逊和 JSON.simple last。

再次从两个不同的角度看这些数字，这是百分比结果:

GSON 显然是赢家。

## 小文件结果:2021

在小文件结果中，Gson 仍然是赢家。显然击败了其他三个竞争者。

结果如下:

1.  Gson
2.  Jsonp
3.  简单
4.  杰克逊

Gson 处理这些文件的速度比下一个候选文件快了将近 200 多毫秒。

## 结论:2021 年

显而易见，java 和 json 库变得更快了。比第一次运行基准测试时快多了。

同样显而易见的是，GSON 加快了步伐，赢得了大文件和小文件的基准测试。在这两种情况下都很明显。