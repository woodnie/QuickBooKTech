## node {#node}

adoop对各个节点的角色定义。

Hadoop分别从三个角度将主机划分为两种角色。

第一，划分为master和slave，即主人与奴隶;

第二，从HDFS的角度，将主机划分为NameNode和DataNode(在分布式文件系统中，目录的管理很重要，管理目录的就相当于主人，而NameNode就是目录管理者);

第三，从MapReduce的角度，将主机划分为JobTracker和TaskTracker(一个job经常被划分为多个task，从这个角度不难理解它们之间的关系)。

Hadoop有官方发行版与cloudera版，其中cloudera版是Hadoop的商用版本，这里先介绍Hadoop官方发行版的安装方法。

Hadoop有三种运行方式：

单节点方式、

单机伪分布方式

集群方式。

乍看之下，前两种方式并不能体现云计算的优势，在实际应用中并没有什么意义，但是在程序的测试与调试过程中，它们还是很有意义的。