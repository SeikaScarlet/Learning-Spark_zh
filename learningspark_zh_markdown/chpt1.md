CHAPTER 1 Introduction to Data Analysis with Spark
***
本章在顶层概述什么是Apach Spark。如果你已很熟悉 Aparch Spark 及其组件，请跳过此章前往第二章。

# 什么是 Apache Spark 

Apache Spark 是一个为*快速*和*通用*性能所设计的集群计算平台。

就运算速度而言， Spark 延续了流行的 MapReduce 模型从而有效的支援多类计算，包括交互式查询(interactive queries)和流式计算(stream processing)。计算速度对于处理大型数据而言极其重要，在交互式数据探究中等上一分钟或一小时意味着截然不同的分析结果。 Spark最主要的特征之一就是可以在内存中进行计算，同时对于一些更为复杂需要依赖磁盘读写的应用程序，这个系统也能提供优于 Mapreduce 的性能。

就通用性而言， Spark 在设计之初考虑到了现已有的各类分布式系统的任务需求，如 batch applications，迭代算法(iterative algorithm)，交互式查询(interactive queries)，以及流式计算(streaming)。在同一引擎下支持这些不同的任务，Spark可以简单且经济的*组装*数据分析生产过程中常用的各类处理类型。此外，Spark减轻了同时维护不同的运维工具所造成管理上的负担。

Spark 在设计上也考虑到了高度可被访问性，提供了简洁的API接口，支持Python，Java，Scala，SQL这些语言，具备丰富的内建库。同时也整合了其他大数据工具。例如，Spark可以在Hadoop集群上运行并且访问任何如Cassandra这样的Hadoop数据源。



# 统一的堆栈 (A unified Stack)

Spark 项目包含了多个相互密切整合的组件。Spark的核心是一个“计算引擎”负责计划、分发、监视多台工作机器(或称为*计算集群*)上执行的计算任务。因为Spark的核心引擎既能高速运算也兼顾通用性，它驱动了多种上层专用任务的组件，如：SQL或机器学习。 这些组件在设计上可以紧密的相互操作，让用户感到像软件项目中的库一样便利的将它们结合起来使用。

紧密整合的设计哲学带了很多好处。 首先，所有的库和堆栈中高层的组件将得益于低层的改善。比如，当Spark的核心引擎被加入一项优化， SQL 和机器学习库也会自动提高运算性能。 其次，堆栈运行所需要的代价已被最小化，不同于同时运行5--10个独立的软件系统，用户只需要部署和运行一个软件系统即可。这里的代价包括了系统部署、维护、测试、支持和其他方面的成本。这意味着每次新添一个组件到Spark的堆栈， Spark 的用户可以立即试用新装的组件。这就将试验一种新数据分析方式的代价从下载、部署、学习一个新软件变为更新Spark即可。

最终，紧密整合的最大好处在于无缝整合不同处理模型的可能。例如，你可以在Spark中从源代码写一个使用机器学习的进行实时分类的模型。同时别的分析师能够实时的通过诸如SQL的方式(如，用非结构化数据结合查询数据)查询结果数据。此外，资深数据工程师和数据科学家可以通过Python shell for ad hoc analysis 访问相同的数据。而与此同时，IT团队正在同一个系统上进行着运维。

在此图1-1简明的列出了Spark的各个组件。

insert fig 1-1 here.

## Spark Core
## Spark SQL0
## Spark Streaming
## Spark MLlib
## GraphX
## Cluster Managers
## Who Uses Spark, and for What?
## Data Science Tasks
## Data Processing Applications

# A Brief History of Spark

# Spark Versions and Releases

# Storage Layers for Spark




