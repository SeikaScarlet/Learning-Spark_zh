***
# 第三章 Programming with RDDs   ||   RDD  编程
***

Ⓔ This chapter introduces Spark’s core abstraction for working with data, the resilient distributed dataset (RDD). An RDD is simply a distributed collection of elements. In Spark all work is expressed as either creating new RDDs, transforming existing RDDs, or calling operations on RDDs to compute a result. Under the hood, Spark automatically distributes the data contained in RDDs across your cluster and parallelizes the operations you perform on them.

Ⓒ 本章介绍 Spark 处理数据的核心抽象：弹性分布式数据集(resilient distributed dataset, RDD)。简单来说 RDD 就是元素的分布式集合。在 Spark 中，所有的工作都被表达为创建新 RDD，对已存在的 RDD 做变换，或者对 RDD 调用某些操作来计算得到一个结果。在底层，Spark 将包含在 RDD 中的数据自动分布到你的整个集群，并将你对其执行的操作并行化。

ⒺBoth data scientists and engineers should read this chapter, as RDDs are the core concept in Spark. We highly recommend that you try some of these examples in an interactive shell (see “Introduction to Spark’s Python and Scala Shells” on page 11). In addition, all code in this chapter is available in the book’s GitHub repository.

Ⓒ 数据科学家和工程师都应该阅读本章，因为 RDD 是 Spark 的核心概念。我们强烈建议你在交互式 Shell 中尝试一些示例（见本书第 11 页的“Spark 的 Python 和 Scala Shell 简介”）。另外，本章所有的代码都在本书的 github 库有下载

# RDD Basics   ||   RDD  基础

Ⓔ An RDD in Spark is simply an immutable distributed collection of objects. Each RDD is split into multiple partitions, which may be computed on different nodes of the cluster. RDDs can contain any type of Python, Java, or Scala objects, including user-defined classes.

Ⓒ Spark 中的 RDD，简单来说就是所有对象的一个不可变的分布式集合。每个 RDD 都被分割为多个分区，这就可以在集群的不同节点上进行计算。RDD 可以包含任何 Python，Java，Scala 对象类型，包括用户自定义类型。

Ⓔ Users create RDDs in two ways: by loading an external dataset, or by distributing a collection of objects (e.g., a list or set) in their driver program. We have already seen loading a text file as an RDD of strings using ```SparkContext.textFile()``` , as shown in Example 3-1.

Ⓒ 用户可以用两种方式创建 RDD：通过加载一个外部数据集，或者在驱动程序中分发一个对象集合（如 list 或 set）。如同示例 3-1 展示的，我们知道了使用SparkContext.textFile()函数加载一个文本文件作为一个字符串 RDD。

*Example 3-1. Creating an RDD of strings with* ```textFile()``` *in Python*
*示例 3-1 ：在 Python 中用* ```textFile()``` *函数创建一个字符串 RDD*

```
>>> lines = sc.textFile("README.md")
```

Ⓔ Once created, RDDs offer two types of operations: transformations and actions. Transformations construct a new RDD from a previous one. For example, one common transformation is filtering data that matches a predicate. In our text file example, we can use this to create a new RDD holding just the strings that contain the word Python, as shown in Example 3-2.

Ⓒ RDD 一旦创建好了，可以提供两种不同类型的操作：*变换操作*(transformation)和*行动操作*(action)。变换操作是从前一个 RDD 构造出一个新的 RDD。例如，有一个常见的变换是用谓词匹配来过滤数据。在我们之前的文本文件的示例中，我们可以用这个变换来创建一个新的 RDD，这个 RDD 容纳的数据是只包含了单词“Python”的字符串。如示例 3-2 所示：

*Example 3-2. Calling the filter() transformation*
示例 3-2 ：调用 ```filter()``` 变换
```
>>> pythonLines = lines.filter(lambda line: "Python" in line)
```

Ⓔ Actions, on the other hand, compute a result based on an RDD, and either return it to the driver program or save it to an external storage system (e.g., HDFS). One example of an action we called earlier is ```first()```, which returns the first element in an RDD and is demonstrated in *Example 3-3*.

Ⓒ 相反，行动操作是基于 RDD 来计算某个结果，并将结果返回给驱动程序或者保存结果到一个外部的存储系统（如 HDFS）。早前我们调用过一个动作的例子是 ```first()```。它返回 RDD 中的第一个元素，*示例 3-3* 展示了这点：

*Example 3-3. Calling the ```first()``` action*
*示例 3-3 ：调用 ```first()``` 动作*
```
>>> pythonLines.first()
u'## Interactive Python Shell'
```

ⒺTransformations and actions are different because of the way Spark computes RDDs. Although you can define new RDDs any time, Spark computes them only in a lazy fashion—that is, the first time they are used in an action. This approach might seem unusual at first, but makes a lot of sense when you are working with Big Data. For instance, consider Example 3-2 and Example 3-3, where we defined a text file and then filtered the lines that include Python. If Spark were to load and store all the lines in the file as soon as we wrote ```lines = sc.textFile(...)```, it would waste a lot of storage space, given that we then immediately filter out many lines. Instead, once Spark sees the whole chain of transformations, it can compute just the data needed for its result. In fact, for the ```first() action``` , Spark scans the file only until it finds the first matching line; it doesn’t even read the whole file.

Ⓒ 变换和动作的区别源于 Spark 对 RDD 的不同计算方式。尽管任何时候你都可以定义一个新的 RDD，但是 Spark 总是以一种惰性(lazy)的方式计算它们，也就是它们被第一次用于动作的时候。刚开始接触到这种方式可能觉得不太寻常，但是当您开始处理大数据时就会有感觉了。举例来说，考虑下前面的*示例 3-2* 和*示例 3-3*，我们定义了一个文本文件 RDD 然后过滤出包含“Python”字符的行。如果当我们一写完 ```lines = sc.textFile(...)``` 语句，Spark 就立刻加载和保存整个文件的所有行的话，考虑到我们马上就要过虑掉很多的行，这会导致浪费很多存储空间。反过来说，一旦Spark知道了整个变换链，它就能只计算结果需要的数据。实际上，对于 ```first()``` 动作来说，Spark 只需要扫描文件直到它找到第一个符合条件的行就可以了，这甚至不需要读整个文件。

########## have revised to here ##########

Ⓔ Finally, Spark’s RDDs are by default recomputed each time you run an action on them. If you would like to reuse an RDD in multiple actions, you can ask Spark to persist it using  RDD.persist() . We can ask Spark to persist our data in a number of different places, which will be covered in Table 3-6. After computing it the first time, Spark will store the RDD contents in memory (partitioned across the machines in your cluster), and reuse them in future actions. Persisting RDDs on disk instead of memory is also possible. The behavior of not persisting by default may again seem unusual, but it makes a lot of sense for big datasets: if you will not reuse the RDD, there’s no reason to waste storage space when Spark could instead stream through the data once and just compute the result. {footnote:The ability to always recompute an RDD is actually why RDDs are called “resilient.” When a machine holding RDD data fails, Spark uses this ability to recompute the missing partitions, transparent to the user.}

Ⓒ 最后，每次你执行个动作，Spark 的 RDD 默认会被重新计算。如果你想在多个动作中重用 RDD，你可以用 RDD.persist()要求 Spark 对 RDD 持久化。我们可以用一些不同的方式要求 Spark 对我们的数据持久化，详见表 3-6。在初次计算之后，Spark 可以保存 RDD 的内容到内存中（在你的集群中跨机器分区），并在未来的动作中重用。持久化 RDD 到磁盘上，而不是内存中，也是可能的。默认不持久化的行为看起来也有点奇怪，但是对大数据集来说就该这样：如果你不会重用这个 RDD，那就没有理由浪费存储空间。相反的，一旦 Spark 流过数据，只是计算结果就好了。 {脚注：总是重新计算一个 RDD 的能力事实上就是为什么 RDD 被称为“弹性”的原因。当拥有 RDD 数据的机器发生故障，Spark 就利用这个能力重新计算丢失的分区，这对用户来说是透明的。}

Ⓔ In practice, you will often use  persist() to load a subset of your data into memory and query it repeatedly. For example, if we knew that we wanted to compute multiple results about the README lines that contain Python, we could write the script shown in Example 3-4.

Ⓒ 实际上，你会经常使用 persist()来加载你的数据子集到内存并反复查询。比如，如果我们知道我们想要计算关于 README 文件中包含“Python”的行的多个结果，我们会写示例 3-4 那样的脚本。

*Example 3-4. Persisting an RDD in memory*
*示例 3-4 ：持久化 RDD 到内存*
```
>>> pythonLines.persist
>>> pythonLines.count()
2
>>> pythonLines.first()
u'## Interactive Python Shell'
```
Ⓔ To summarize, every Spark program and shell session will work as follows:
1. Create some input RDDs from external data.
2. Transform them to define new RDDs using transformations like  filter() .
3. Ask Spark to  persist() any intermediate RDDs that will need to be reused.
4. Launch actions such as  count() and  first() to kick off a parallel computation,
which is then optimized and executed by Spark.

Ⓒ 总之，每个 Spark 程序或者 shell 会话都是像这样工作：
1. 从外部数据创建一些作为输入的 RDD；
2. 使用类似 ```filter()``` 之类的变换来定义出新的 RDD‘
3. 要求 Spark 对需要重用的任何中间 RDD 进行 ```persist()```；
4. 启动类似 ```count()``` 和 ```first()``` 的动作开始并行计算，然后 Spark 会优化并执行。

> Ⓔ ```cache()``` is the same as calling ```persist()``` with the default storage
level.

> Ⓒ ```cache()``` 和在默认存储级别上和调用 ```persist()``` 的效果一样。

Ⓔ In the rest of this chapter, we’ll go through each of these steps in detail, and cover some of the most common RDD operations in Spark.

Ⓒ 在本章接下来的部分，我们将从头到尾的详细讨论每个步骤，包括 Spark 中一些最常用的操作。

# Creating RDDs   ||   创建 RDD

Ⓔ Spark provides two ways to create RDDs: loading an external dataset and parallelizing a collection in your driver program.

Ⓒ Spark 提供两种方式创建 RDD：加载一个外部数据集，或者在你的驱动程序中并行化一个数据集合。

Ⓔ The simplest way to create RDDs is to take an existing collection in your program and pass it to SparkContext’s  parallelize() method, as shown in Examples 3-5 through 3-7. This approach is very useful when you are learning Spark, since you can quickly create your own RDDs in the shell and perform operations on them. Keep in mind, however, that outside of prototyping and testing, this is not widely used since it requires that you have your entire dataset in memory on one machine.

Ⓒ 最简单的创建 RDD 的方式就是将你程序中已存在的集合传递给 SparkContext 的 ```parallelize()``` 方法，见*示例 3-5* 到 *3-7*。当你在学习 Spark 的时候，这种方法非常有用。你可以在 Shell 中快速创建你自己的 RDD 并对其进行操作。请记住，在创建原型和测试之外，这种方式并不常用，因为它会要求所整个数据集都在一台机器上的内存中。

Example 3-5. ```parallelize()``` method in Python
示例 3-5 ： Python 的 parallelize() 方法
```
lines = sc.parallelize(["pandas", "i like pandas"])
```

Example 3-6. ```parallelize()``` method in Scala
示例 3-6 ： Scala 的 parallelize() 方法
```
val lines = sc.parallelize(List("pandas", "i like pandas"))
```

Example 3-7. ```parallelize()``` method in Java
示例 3-7 ： Java 的 parallelize() 方法
```
JavaRDD<String> lines = sc.parallelize(Arrays.asList("pandas", "i like pandas"));
```

Ⓔ A more common way to create RDDs is to load data from external storage. Loading external datasets is covered in detail in Chapter 5. However, we already saw one method that loads a text file as an RDD of strings,  SparkContext.textFile() , which is shown in Examples 3-8 through 3-10.

Ⓒ 更常见的方式是从外部存储加载数据，详见第 5 章。然而我们之前已经见过加载
文本文件为字符串 RDD 的方法:SparkContext.textFile()，见示例 3-8 到 3-10。

Example 3-8. textFile() method in Python
示例 3-8 ： Python 的 textFile() 方法
```
lines = sc.textFile("/path/to/README.md")
```

Example 3-9. textFile() method in Scala
示例 3-9 ： Scala 的 textFile() 方法
```
val lines = sc.textFile("/path/to/README.md")
```

Example 3-10. textFile() method in Java
示例 3-10 ： Java 的 textFile() 方法
```
JavaRDD<String> lines = sc.textFile("/path/to/README.md");
```

# RDD Operations

## Transformations
## Actions
## Lazy Evaluation

# Passing Functions to Spark

## Python
## Scala
## Java

# Common Transformations and Actions

## Basic RDDs
## Converting Between RDD Types

# Persistence (Caching)
# Conclusion
Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

Ⓔ

Ⓒ 

