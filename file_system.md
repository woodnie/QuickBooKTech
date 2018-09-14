# File System {#file-system}

### Distributed File System {#distributed-file-system}

#### Hadoop {#hadoop}

[http://hadoop.apache.org/common/docs/r0.19.2/cn/quickstart.html](http://hadoop.apache.org/common/docs/r0.19.2/cn/quickstart.html)

一个分布式系统基础架构，由Apache基金会开发。用户可以在不了解分布式底层细节的情况下，开发分布式程序。充分利用集群的威力高速运算和存储。Hadoop实现了一个分布式文件系统（Hadoop Distributed File System），简称HDFS。HDFS有着高容错性的特点，并且设计用来部署在低廉的（low-cost）硬件上。而且它提供高传输率（high throughput）来访问应用程序的数据，适合那些有着超大数据集（large data set）的应用程序。HDFS放宽了（relax）POSIX的要求（requirements）这样可以流的形式访问（streaming access）文件系统中的数据。

Hadoop 是一个能够对大量数据进行分布式处理的软件框架。

Hadoop实现了一个分布式文件系统（Hadoop Distributed File System），简称HDFS。HDFS有着高容错性的特点，并且设计用来部署在低廉的（low-cost）硬件上。而且它提供高传输率（high throughput）来访问应用程序的数据，适合那些有着超大数据集（large data set）的应用程序。

HBase

[http://hbase.apache.org/](http://hbase.apache.org/)

HBase is the Hadoop database. Think of it as a distributed scalable Big Data store.

#### Lustre {#lustre}

Lustre File System 【转载】

历史

Lustre 是HP，Intel，Cluster File System 公司联合美国能源部开发的Linux集群并行文件系统。它来源于卡耐基梅隆大学的NASD 项目研究工作。Lustre 文件系统2003 年推出 了1.0 版，目前已经推出了1.4.7 的发布版本。Lustre 在美国能源部(U.S.Department of Energy：DOE)、Lawrence Livermore国家实验室，Los Alamos 国家实验室，Sandia 国家实验室，Pacific Northwest国家实验室的高性能计算系统中已得到了初步的应用，IBM 正在研制的Blue Gene系统也将采用Lustre 文件系统实现其高性能存储。HP 公司的&quot;StorageWorksScalable File Share&quot;（HP SFS，可扩展文件共享），是首款采用Lustre 技术的商业化产品。作为首个开源的基于对象存储设备的分布式并行文件系统，Lustre 可以说是性能优异，并被越来越广泛的应用。

系统架构

图1 Lustre 的系统架构

Lustre 是一个透明的全局文件系统，客户端可以透明地访问集群文件系统中的数据，而无需知道这些数据的实际存储位置。其结构如图1 所示，Lustre 由客户端，两 个MDS（一个运行，一个备份）和OST 设备池，通过高速的以太网或QWS Net（QUALCOMM Wireless Systems）所构成。Lustre 最多可以支持多达10000个客户端；两个MDS 采用共享存储设备的Active－Standby 方式的容错机制； 存储设备跟普通的，基于块的IDE 存储设备不同，是基于对象的智能存储设备。客户端在需要访问文件系统的文件数据时，先访问MDS，获取文件相关的元数据信息，然后就直接和相关的OST 通信，取得文件的实际数据。

客户端通过网络读取服务器上的数据，存储服务器负责实际文件系统的读写操作以及存储设备的连接，元数据服务器负责文件系统目录结构、文件权限和文件的扩展 属性以及维护整个文件系统的数据一致性和响应客户端的请求。由于Lustre采 用元数据和存储数据相分离的技术，可以充分分离计算和存储资源，使得客户端计算机可以专注于用户和应用程序的请求；存储服务器和元数据服务器专注于读、传 输和写数据。存储服务器端的数据备份和存储配置以及存储服务器扩充等操作不会影响到客户端，存储服务器和元数据服务器均不会成为性能瓶颈。 Lustre 的全局命名空间为文件系统的所有客户端提供了一个有效的全局唯一的目录树。全局目录树消除了在客户端的配置信息，并且在配置信息更新时仍然保持有效。 运行机制 图2 Lustre三个组成部分间的关系 Lustre文件系统是一个高度模块化的系统，主要由三个部分组成：客户端（Client）、对象存储服务器（Object Storage Target，OST）和元数据服务器（MetaData Server，MDS）。三个组成部分除了各自的独特功能外，相互之间共享诸如锁、请求处理、消息传递等模块。为了提高 Lustre 文件系统的性能，通常 Client、OST 和 MDS 是分离，当然这些子系统也可以运行在同一个系统中。 客户端：通过标准的POSIX接口向用户提供对文件系统的访问。对于客户端而言。Client同OST进行文件数据的交互，包括文件数据的 读写、对象属性的改变等；同MDS进行元数据的交互，包括目录管理、命名空间管理等。 OST：在Lustre中，OST负责实际数据的存储，处理所有客户端和物理存储之间的交互。这种存储是基于对象（Object -based）的，OST将所有的对象数据放到物理存储设备上，并完成对每个对象的管理。OST和实际的物理存储设备之间通过设备驱动程序来实现交互。通 过驱动程序的作用，Lustre可以继承新的物理存储技术以及文件系统，实现对物理存储设备的扩展。为了满足高性能计算系统的需要，Lustre针对大文 件的读写进行了优化，为集群系统提供较高的I/O吞吐率。存储在OST上的文件可以是普通文件，也可以是复制文件。Lustre同

时还将数据条块化，再把 数据分配到各个存储服务器上，提供了比传统 SAN 的&quot;块共享&quot;更为灵活和可靠的共享访问方式。当某个存储节点出现故障时，客户端仍然能够通过 MDS：在Lustre中，元数据的管理由MDS负责。MDS负责向客户端提供整个文件系统的元数据，管理整个文件系统的命名空间，维护整 个文件系统的目录结构、用户权限，并负责维护文件系统的数据一致性。通过MDS的文件和目录访问管理，Lustre可以控制客户端对文件系统中文件的创 建、删除、修改以及对目录的创建、删除、修改等访问控制。通过MDS，客户端得到数据所在的OST，并与其建立连接，此后的读写操作就在客户端同OST之 间进行，除非有对命名空间的修改，将不再同MDS有关系，这样就降低了MDS的负载。在多个客户端的情况下，由于有多个OST存在，上述的工作模式就把对 文件系统的访问转换为并行操作，从而可以较好地提高性能。在Lustre中，客户端使用写回式Cache来保证元数据的一致性。Lustre系统可以配置 两个MDS服务器，其中一个作为备份。两个服务器采用共享存储的方式来存放元数据。当某个MDS出现故障后，备份服务器可以接管其服务，保证系统的正常运 行。Lustre打算将来实现多元数据服务器来提高元数据处理的性能和可扩展性。 图3 一个简单mkdir的过程 如图3所示，Lustre中的&quot;mkdir&quot;命令的执行需要经过如下几个步骤：客户端首先向MDS申请&quot;mkdir&quot;操作，MDS先锁定该操作的父目录， 并添加目录，成功后把目录锁返还给客户端，然后客户端再和具体的文件服务器通信，创建相关的目录

错误恢复 Lustre在设计上考虑了对网格环境的支持，一方面它考虑了文件系统的安全性策略，包括认证、授权和文件内容加密三个方面；另一方面它考虑在管理与系统 状态监控方面与网格的结合，其配置信息和状态信息采用XML格式，提供通过LDAP（Light-Weight Directory Access Protocol)接口操纵配置信息，而且可以支持通过SNMP来获取和修改这些信息。 图4 MDS错误恢复 Lustre在设计时也充分考虑了系统故障时的错误恢复情况，如图4所示，系统正常运行时，存在一台前台的活跃MDS服务器和一台备用MDS服务器。当前 台运行的MDS服务器出现故障时，客户端会通过查询LDAP服务器，自动转而连接备用MDS服务器，从而使系统重新恢复正常运行。 性能总结 从初步的测试看，Lustre的性能和可扩展性可以说都是相当优秀。以下是Lustre的并发写文件的速率和并发创建文件的速率与当今应用的主流文件系统 的对比。

可以说，在文件系统的主要性能指标方面，Lustre都大幅的超越对手（GoogleFS是单个公司的产品，无法加入比较），实现了可靠性的，可用性的， 可扩展性的，可管理性的，高性能的，海量的，分布式的数据存储，并且能够按照应用需求的不同提供不同的服务，如不同的应用、不同的客户端环境、不同的性能 等，真正实现了按需服务。

#### MFS {#mfs}

MooseFS

#### Bigtable {#bigtable}

Bigtable 是一个分布式的结构化数据存储系统，它被设计用来处理海量数据：通常是分布在数千台普通服务器上的PB级的数据。Google 的很多项目使用Bigtable存储数据，包括Web索引、Google Earth、Google Finance。这些应用对Bigtable提出的要求差异非常大，无论是在数据量上（从URL到网页到卫星图像）还是在响应速度上（从后端的批量处理到实时数据服务）。尽管应用需求差异很大，但是，针对Google的这些产品，Bigtable还是成功的提供了一个灵活的、高性能的解决方案。本论文描述了Bigtable提供的简单的数据模型，利用这个模型，用户可以动态的控制数据的分布和格式；我们还将描述Bigtable的设计和实现。

#### Google File System {#google-file-system}

The Google File System 中文版 [http://os.51cto.com/art/201008/218364.htm](http://os.51cto.com/art/201008/218364.htm)

Linux GFS中的GFS是Global FileSystem，指的是全局文件系统，要解决的问题是共享存储的读写。如下图：

Linux GFS类似于一个并发锁的处理器：获得独占锁的节点才可以进行写操作。

所以，Linux GFS面对的存储设备有两种：iSCSI和FC

Google GFS中的GFS是Google FileSystem，指的是分布式文件系统，要解决的问题是文件系统的分布。如下图所示【下面的图是HDFS的，架构类似】：

Google GFS是一个分布式文件系统，除了管理节点外，其它的都是数据节点；数据节点存放具体的数据。

总结：

Linux GFS是把让昂贵的存储共享起来给大家用；

Google GFS是把便宜的各个本地存储集中起来共享给大家用。

#### Global FileSystem {#global-filesystem}

### Local File System {#local-file-system}

#### EXT3 {#ext3}

#### EXT4 {#ext4}

### Search Engine Optimization {#search-engine-optimization}