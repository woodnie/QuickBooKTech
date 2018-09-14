## CLARiiON远程复制软件简介 {#clariion}

created by [Roger W.](https://community.emc.com/people/Roger_Wu) on Apr 25, 2012 2:00 AM, last modified by [Roger W.](https://community.emc.com/people/Roger_Wu) on Apr 26, 2012 9:19 PM            

                [                    Version 6                ](https://community.emc.com/docs/DOC-16304/diff?secondVersionNumber=6)            

**CLARiiON远程复制软件简介**

介绍

CLARiiON提供了一组远程复制产品，专门用于解决客户环境中的各种业务问题。

这些产品包括：

         MirrorView/Synchronous，用于无数据丢失的镜像同步；

         MirrorView/Asynchronous，用于实现基于阵列的异步复制；

         RecoverPoint/SE，用于以一流的数据压缩和网络带宽利用率实现可扩展且无距离限制的数据复制；

         SAN Copy，用于在异构存储阵列之间跨SAN或WAN执行高速数据移动。

更多信息

**MirrorView/Synchronous**

MirrorView/Synchronous (MirrorView/S)可以跨一定区域(园区或市区内)提供高可用的数据保护。通过在CLARiiON系统之间保持同步数据镜像，MirrorView/S可为重要的业务部门确保数据可用性。MirrorView/S是基于阵列的，因此它不使用任何服务器资源。MirrorView/S与SnapView共同为在线数据可用性以及灾难恢复提供了一种独特的解决方案。

在MirrorView/S配置中，服务器同时向源阵列和远程阵列写入数据。数据写入到源阵列与远程阵列上之后，就会向服务器发回确认信息，以确保两个阵列上有完整的事务记录。

**MirrorView/Asynchronous**

MirrorView/Asynchronous (MirrorView/A)可跨州或全球(没有距离限制)提供高可用的数据存储。与MirrorView/S一样，MirrorView/A也是基于阵列的，因此它也不使用任何服务器资源。MirrorView/A与SnapView结合，为在线数据可用性以及灾难恢复提供了一种独特的解决方案。

在MirrorView/A配置中，服务器向源阵列写入数据，源阵列立即确认该写入操作。然后数据可以在后台写入到远程CLARiiON系统。得到的镜像可用于到目标站点的快速故障切换。

**RecoverPoint/SE**

RecoverPoint/SE使用了与常规RecoverPoint解决方案相同的技术，但它是专门针对CLARiiON环境设计的，为客户复制和保护在CLARiiON阵列上整合的信息提供了一个全面的解决方案。

RecoverPoint/SE高效、基于网络的同步和异步复制补充了CLARiiON解决方案。它支持光纤通道和/或iSCSI环境，可以优化带宽利用率，根据吞吐量限制和延迟情况在同步和异步模式之间动态地切换，并可以使用CLARiiON阵列上的RecoverPoint写拆分功能在不影响存储性能的情况下部署。

EMC的数据保护方法支持一些关键功能，如可利用跟踪所有数据更改的历史日志和识别特定于应用程序事件的书签，即时将数据恢复到任一时间点。RecoverPoint/SE利用一致性组使用户可以定义卷集，而要定义卷集就必须保持复制和恢复期间写入操作之间的顺序。另外，RecoverPoint/SE减少了网络带宽需求，具体就是通过一个策略引擎，它在跨网络发送数据之前确定该压缩多少数据，以及如何排定网络资源的优先级。

**SAN Copy**

SAN Copy极为灵活，使您能够配置可满足特定业务需求的环境。SAN Copy运行在CLARiiON网络存储系统上，通过WWN (World Wide Name)和/或端口/LUN 号的组合与其他存储系统进行通讯。数据移动在数据块级别执行，以便可通过SAN或WAN进行高速拷贝。

SAN Copy运行在CX4、CX3、CX700、CX500、CX600和CX400等系统上，并且可以从这些阵列中将数据的完整或增量拷贝“推送”到任何受支持的EMC 或第三方阵列中。增量更新速度更快，并可减少通过网络传输的数据总量，因为仅拷贝自最后一次SAN Copy会话后的更改部分。这些阵列上的SAN Copy还可以从任何受支持的阵列中“拉入”完整的数据拷贝。

参考

点击[这里](http://china.emc.com/collateral/software/data-sheet/c1149-cx-remote-replication.pdf)获取产品说明文档”EMC CLARiiON 远程复制软件”以了解更多信息。

应用于

CLARiiON CX系列，VNX系列