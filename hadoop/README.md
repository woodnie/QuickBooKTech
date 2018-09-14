# Hadoop {#hadoop}

（1）MapReduce：古老的分布式计算框架，它的特点是扩展性、容错性好，易于编程，适合离线数据处理，不擅长流式处理、内存计算、交互式计算等领域。MapReduce网址是： [http://hadoop.apache.org/](http://hadoop.apache.org/)

（2）Hive：披着SQL外衣的MapReduce。Hive是为方便用户使用MapReduce而在外面包了一层SQL，由于Hive采用了SQL，它的问题域比MapReduce更窄，因为很多问题，SQL表达不出来，比如一些数据挖掘算法，推荐算法、图像识别算法等，这些仍只能通过编写MapReduce完成。Hive网址是： [http://hive.apache.org/](http://hive.apache.org/)

（3）Pig：披着脚本语言外衣的MapReduce，为了突破Hive SQL表达能力的限制，采用了一种更具有表达能力的脚本语言PIG。由于pig语言强大的表达能力，Twitter甚至基于Pig实现了一个大规模机器学习平台（参考Twitter在SIGMOD2012的文章&quot;Large-Scale Machine Learning at Twitter&quot;）。Pig网址是： [http://pig.apache.org/](http://pig.apache.org/)

（4）Stinger Initiative（Tez optimized Hive）：Hortonworks开源了一个DAG计算框架Tez，该框架可以像MapReduce一样，可以用来设计DAG应用程序，但需要注意的是，Tez只能运行在YARN上。Tez的一个重要应用是优化Hive和PIG这种典型的DAG应用场景，它通过减少数据读写IO，优化DAG流程使得Hive速度提供了很多倍。（Stinger正在开发中，Tez代码： [https://svn.apache.org/repos/asf/incubator/tez/branches/](https://svn.apache.org/repos/asf/incubator/tez/branches/) ）

（5）Spark：为了提高MapReduce的计算效率，伯克利开发了spark，spark可看做基于内存的MapReduce实现，此外，伯克利还在Spark基础上包了一层SQL，产生了一个新的类似Hive的系统Shark，但目前Spark和Shark尚属于实验室产品。Spark网站是： [http://spark-project.org/](http://spark-project.org/)

（6）Storm/S4：Hadoop在实时计算/流式计算领域（MapReduce假设输入数据是静态的，处理过程中不能被修改，而流式计算则假设数据源是流动的，数据会源源不断流入系统），一直比较落后，还好，Twitter开源的Storm和yahoo！开源的S4弥补了这一缺点，Storm在淘宝，mediaV等公司得到广泛的应用。Storm网址是： [http://storm-project.net/](http://storm-project.net/) ，S4网址是： [http://incubator.apache.org/s4/](http://incubator.apache.org/s4/)

（7）Cloudera Impala/Apache drill：Google Dremel的开源实现，也许是因为交互式计算需求太过强烈，发展迅猛，impala仅用了一年左右便推出1.0GA版本。这种系统适用于交互式处理场景，最后产生的数据量一定要少。Impala尽管发布了1.0版本，但在容错性、扩展性、支持自定义函数等方面，有很长的路要走。Cloudera Impala网址是： [https://github.com/cloudera/impala](https://github.com/cloudera/impala) ，Apache drill网址是： [http://incubator.apache.org/drill/](http://incubator.apache.org/drill/) 。

Hortonworks将应用需求进行了如下划分：

映射到上面几种系统，可知：

（1）实时应用场景(0~5s)：Storm、S4、Cloudera Impala，Apache Drill等；

（2）交互式场景（5s~1m）：这种场景通常能要求必须支持SQL，则可行系统有：Cloudera Impala、Apache Drill、Shark等；

（3）非交互式场景（1m~1h）：通常运行时间较长，处理数据量较大，对容错性和扩展性要求较高，可行系统有：MapReduce、Hive、Pig、Stinger等；

（4）批处理场景（1h+）：通常运行时间很长，处理数据量很大，对容错性和扩展性要求很高，可行系统有：MapReduce、Hive、Pig、Stinger等。