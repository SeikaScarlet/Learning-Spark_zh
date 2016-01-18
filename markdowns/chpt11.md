***
# Chapter 11 Machine Learning with MLlib
***

Ⓔ MLlib is Spark 's library of machine learning functions. Designed to run in parallel on clusters, MLlib contains a variety of learning algorithms and is accessible from all of Sparks programming languages. This chapter will show you how to call it in your own programs, and offer common usage tips.

Ⓒ MLib是Spark上实现机器学习函数集的库。MLib被设计成能在集群上并行运行，其中包含了大量的学习算法，并可被spark所有编程语言调用。本章将向您讲解如何在程序中调用Mlib，以及该库常见的使用方法。

Machine learning itself is a topic large enough to fill many books [1][footnote Some examples from O'Reilly included Machine Learning with R and Machine Learning for Hackers.], so unfortunately, in this chapter, we will not have the space to explain machine learning in detail. If you are familiar with machine learning, however, this chapter will explain how to use it in Spark; and even if you are new to it, you should be able to combine the material here with other introductory material. This chapter is most relevant to data scientists with a machine learning background looking to use Spark, as well as engineers working with a machine learning expert.
机器学习本身就是一门博大精深的学科，因此很遗憾我们无法在本书中向您一一道尽机器学习。相反，如果您已经很熟悉机器学习，这章将向您阐述如何用Spark进行机器学习；但是，如果你对机器学习还很陌生，你可能需要将本章的内容结合到其它机器学习导论中理解。本章的内容面向具备机器学习背景而想使用spark的数据科学家，以及与那些与机器学习专家团队协作的数据工程师。
# Overview    ||   综述

MLlib's design and philosophy are simple: it lets you invoke various algorithms on distributed datasets, representing all data as RDDs. MLlib introduces a few data types (e.g., labeled points and vectors), but at the end of the day, it is simply a set of functions to call on RDDs. Fore example, to use MLlib for a text classification task (e.g., identifying spammy emails), you might do  the following:

1. Start with a RDD of strings representing your messages.
2. Run on of MLlib's *feture extraction* algorithms to convert text into numerical features (suitable for learning algorithms); this will give back an RDD of vectors.
3. Call a classification algorithms (e.g., Logistic regression) on the RDD of vectors; this will give back a model object that can be used to classify new points.
4. Evaluate the model on a test dataset using one of MLlib's evaluation functions.

MLib 的设计哲学很简约：用 RDD 代表所有的数据，而用户则在分布式的数据集上运行各种算法。MLib引入了几个数据类型（如，labled points和vectors），但最终，它只是简单的一组可在RDDs上调用的函数。比如，要用 MLib 去实现文本分类（识别垃圾邮件），你可能要做以下几步：

1. 从一组包含字符串信息的 RDD 开始， 用它代表你要分类的文本数据；
2. 调用 MLlib 中的一个*特征提取*算法，将文字信息转换问数字特征（因为它将很便于学习算法处理），这将返回一个包含特征向量的RDD；
3. 	基于RDD的特征向量调用一个分类算法（如逻辑回归）；它将返回一个用于识别新输入特征向量点的模型对象。
4. 	使用Mllib的某个评估函数，在一个测试数据集上评估这个模型。

One important thing to note about MLlib is that it contains only *parallel* algorithms that run well on clusters. Some classic ML algorithms are not included because they were not designed for parallel platforms, but in contrast MLlib contains several recent research algorithms for clusters, such as distributed random forests, K-means||, and alternating least squares. This choice means that MLlib is best suited for running each algorithm on a large dataset. If you instead have many small datasets on which you want to train different learning models, it would be better to use a single-node learning library (e.g., Weka or SciKit-Learn) on each node, perhaps calling it in parallel across nodes using a Spark ```map()```. Likewise, it is common for machine learning pipelines to require training the *same* algorithm on a small dataset with many configurations of parameters, in order to choose the best one. You can achieve this in Spark by using ```paralleize()``` over your list of parameters to train different ones on different nodes, again using a single-node learning library on each node. But MLlib itself shines when you have a large, distributed dataset that you need to train model on.

值得注意的是，MLib所包含的仅仅是那些能在集群上良好并行运行的算法。一些经典的机器学习算法不是为并行运算所设计的，故而没有包含在MLlib内。相反，MLlib包含了几个为集群并行计算而设计的新算法，如分布式随机森林（distributed random forests）、K均值（K-Means），和交替(??)最小二乘法（alternating least squares）。这种编排意味着MLlib是最适合于在大数据集上运行这些算法的工具。如果你有一些小数据集想要训练不同的学习模型，那么使用单节点模式的机器学习库会更好一些（如，Weka 或 SciKit-Learn ），或者使用 ```Spark map()``` 跨节点并行调用。同样的，为了找出最优的参数配置，相同的算法往往会在小数据集上先以不同参数进行训练。您可以在Spark 上用一个参数列表 list（作为输入）运行 ```parallelize()``` 去在不同的节点上训练不同参数配置，然后着在每个节点上运行单节点机器学习库。当你需要用模型训练一个大型的分布式数据集的时候，MLlib的表现将会脱颖而出。

Finally, in Spark 1.0 and 1.1, MLlib's interface is relatively low-level, giving you the functions to call for different tasks but not the higher-level workflow typically required for a learning pipeline (e.g., splitting the input into training and test data, or trying many combinations of parameters). In Spark 1.2, MLlib gains a additional (and at the time of writing still experimental) *pipeline API* for building such pipelines. This API resembles higher-level libraries like SciKit-Learn, and will hopefully make it easy to write complete, self-tuning pipelines. We include a preview of this API at the end of this chapter, but focus primarily on the lower-level APIs.

最后要说明的是，在 Spark 1.0 和 1.1 中，MLlib 的接口相对比较低级，仅给用户调用不同任务的函数，而不会有机器学习工作流程中所需的更高一级的控制（如将输入数据分离为训练和测试两组，或是测试每个组合的参数配置）。在 Spark 1.2 中MLlib提供了一个附加的（并且目前还在试验阶段的）*流程控制 API* ，用于高级的流程控制。这个 API 组件重新组合了像 SciKit-Learn 这样高级机器学习库， 从而希望简化流程控制，实现自我调优。我们本章主要探讨低级别的API，并会在本章末介绍高级别的API。

＝＝＝
＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃
＃＃＃＃  I， Seika， input this chapter to here 
＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃


































