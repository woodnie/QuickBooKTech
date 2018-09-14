# Storage {#storage}

### NAS {#nas}

### DAS {#das}

### SAN {#san}

### IP SAN {#ip-san}

#### iSCSI {#iscsi}

iSCSI （发音为 / а?sk?zi/ ）又称为IP-SAN，是一种基于因特网及SCSI-3协议下的存储技术，由IETF提出，并于2003年2月11日成为正式的标准。与传统的SCSI技术比较起来，iSCSI技术有以下三个革命性的变化：

把原来只用于本机的SCSI协同透过TCP/IP网络传送，使连接距离可作无限的地域延伸；

连接的服务器数量无限（原来的SCSI-3的上限是15）；

由于是服务器架构，因此也可以实现在线扩容以至动态部署。

iSCSI（iSCSI = internet Small Computer System Interface ）是由IEETF开发的网络存储标准，目的是为了用IP协议将存储设备连接在一起。通过在IP网上传送SCSI命令和数据，ISCSI推动了数据在网际之间的传递，同时也促进了数据的远距离管理。由于其出色的数据传输能力，ISCSI协议被认为是促进存储区域网（SAN）市场快速发展的关键因素之一。因为 IP网络的广泛应用， ISCSI能够在LAN、WAN甚至internet上进行数据传送，使得数据的存储不再受地域的现在。

iSCSI存储技术全攻略: [http://www.sansky.net/article/2007-12-03-iscsi-storage.html](http://www.sansky.net/article/2007-12-03-iscsi-storage.html)

iSCSI 是一种在Internet协议上,特别是以太网上进行数据块传输的标准,它是一种基于IP Storage理论的新型存储技术，该技术是将存储行业广泛应用的SCSI接口技术与IP网络技术相结合，可以在IP网络上构建SAN存储区域网，简单地说，iSCSI就是在IP网络上运行SCSI协议的一种网络存储技术。iSCSI技术最初由Cisco和IBM两家发起，并且得到了广大IP存储技术爱好者的大力支持。这几年迅速的发展壮大了起来。

对于中小企业的存储网络来说，iSCSI是个非常好的选择，首先，从技术实现来讲，iSCSI是基于IP协议的技术标准，它允许网络在TCP/IP协议上传输SCSI命令，实现了SCSI和TCP/IP协议的连接，这样用户就可以通过TCP/IP网络来构建存储区域网，它只需要不多的投资，就可以方便、快捷地对信息和数据进行交互式传输和管理。但是在iSCSI出现之前，构建存储区域网的唯一技术是利用光纤通道，而这要花费很大的建设成本，一般中小企业是无法承担的，其次iSCSI技术解决了传输效率、存储容量、兼容性、开放性、安全性等诸多问题，在使用性能上绝对不输给商业的存储系统或者光纤存储网络。

iSCSI 的优势主要表现为：首先，iSCSI沿用TCP/IP协议，而TCP/IP是在网络方面最通用、最成熟的协议，且IP网络的基础建设非常完善，同时，SCSI技术是被磁盘、磁带等设备广泛采用的存储标准，这两点使iSCSI的建设费用和维护成本非常低廉;其次，iSCSI支持一般的以太网交换机而不是特殊的光纤通道交换机，从而减少了异构网络带来的麻烦;最后，iSCSI是通过IP封包传输存储命令，因此可以在整个Internet上传输，没有距离的限制。

一个简单的iSCSI系统大致有以下部分组成：

? iSCSI initiator或者iSCSI HBA

? iSCSI target

? 以太网交换机

? 一台或者多台服务器

#### iSCSI initiator {#iscsi-initiator}

iSCSI initiator 是一个安装在计算机上的一个软件或是一个硬件设备，它负责处理同iSCSI存储设备进行通信。

iSCSI 服务器与iSCSI存储设备之间的连接方式有两种：

    第一种是基于软件的方式，也就是iSCSI initiator，在iSCSI服务器上安装initiator后，Initiator软件可以将以太网卡虚拟为iSCSI卡，进而接受和发送 iSCSI数据报文，从而实现主机和iSCSI存储设备之间的iSCSI协议和TCP/IP协议传输功能。这种方式只需以太网卡和以太网交换机，无需其它设备，因此成本是最低的，但是iSCSI包文和TCP/IP包文转换需要消耗iSCSI服务器的一部分cpu资源，只有在低I/O和低带宽性能要求的应用环境中才能使用这种方式。

    第二种是硬件iSCSI HBA（Host Bus Adapter）卡方式，即为硬件iSCSI initiator，这种方式需要购买iSCSI HBA卡，然后安装在iSCSI服务器上，从而实现iSCSI服务器与交换机之间、iSCSI服务器与存储设备之间的高效数据传输。与第一种方式相比，硬件iSCSI HBA卡方式不需要消耗iSCSI服务器的CPU资源，同时硬件设备是专用的，所以基于硬件的iSCSI initiator可以提供更好的数据传输和存储性能。但是，iSCSI HBA卡价格比较昂贵，因而，要在性能和成本之间进行权衡。

iSCSI initiator软件一般都是免费的，Centos和RHEL对iSCSI Initiator支持非常不错，现在的Linux发行版本都默认已经自带了iSCSI Initiator。

#### iSCSI target {#iscsi-target}

一个可以被用于存储数据的iSCSI磁盘阵列或者具有iSCSI功能的设备都可以被称为&quot;iSCSI target&quot;，因为对于大多数操作系统来说，都可以用一些软件将系统转变为一个&quot;iSCSI target&quot;，本章我们重点讲述的就是如何构建一个PC构架的iSCSI存储系统，所谓PC构架就是选择一个普通的、性能优良的、可支持多块磁盘的 PC（一般为PC服务器），选择一款相对成熟稳定的iSCSI target软件，将iSCSI Target软件安装在PC服务器上，这样普通的PC服务器就转变成一台iSCSI存储设备，并通过PC服务器的以太网卡对外提供iSCSI数据传输服务。

目前大多数iSCSI target软件都是收费的，例如DataCore Software的SANmelody，FalconStor Software的iSCSI Server for Windows等，这些都是windows平台的，不过，也有一些linux平台开源的iSCSI target软件，例如iSCSI Enterprise Target，在下面章节会重点介绍这个软件。

利用iSCSI target软件，可以将服务器的存储空间分配给客户机使用，客户机就可以像使用本地硬盘一样使用iSCSI磁盘，包括对其进行分区，格式化，读写等。并且每个客户端都可以往iSCSI磁盘写数据，互不干扰，且不会破坏存储服务器的数据。同时，iSCSI target软件对用户权限控制非常灵活，支持配置文件。

#### Structure {#structure}

[http://blog.chinaunix.net/uid-509190-id-3051015.html](http://blog.chinaunix.net/uid-509190-id-3051015.html)

~

利用 ISCSI 存储技术构建 IP 存储网络（实战篇） (2011-12-29 16:13)

本文重点介绍如何构建一个 PC 构架的 iSCSI 存储系统，这里我们选择一个普通的、性能优良的、可支持多块磁盘的 PC 服务器作为 iSCSI target ，并且选择一个成熟稳定的 iSCSI target 软件 iscsitarget ，基本配置环境如表 1 所示： 表 1

[\\t &quot;_blank&quot;](http://blog.chinaunix.net/link.php?url=http://blog.chinaunix.net%2Fattachment%2F201112%2F29%2F509190_13251465910QVc.png)

这里将 Target 主机第三块硬盘（硬盘标识为 /dev/sdc ）作为 iSCSI 共享磁盘，硬盘大小为 10G ，分别共享给一台 windows 主机和一台 Linux 主机，基本结构如图 1 所示：

[\\t &quot;_blank&quot;](http://blog.chinaunix.net/link.php?url=http://blog.chinaunix.net%2Fattachment%2F201112%2F29%2F509190_13251466041eEZ.png)

图 1

下面开始详细介绍 iSCSI 网络存储的搭建过程。

**一、安装** **iSCSI target** **软件** 安装 iscsitarget 软件是在 Target 主机上进行的，即上面设定的 192.168.12.246 主机，这里我们选择的 target 软件是 iscsitarget ，读者可以从 [\\t &quot;_blank&quot;](http://blog.chinaunix.net/link.php?url=http://iscsitarget.sourceforge.net%2F) http://iscsitarget.sourceforge.net 下载相应的版本，这里下载的是 iscsitarget-1.4.20.1.tar.gz ，接着开始进行编译安装： [root@iscsi-target iscsi]#tar -xzvf iscsitarget-1.4.20.1.tar.gz[root@iscsi-target iscsi]#cd iscsitarget-1.4.20.1[root@iscsi-target iscsitarget-1.4.20.1]#make[root@iscsi-target iscsitarget-1.4.20.1]#make install 安装完毕后，会创建 /etc/iet/ 目录，此目录下有 Iscsitarget 的相关配置文件，接着就可以启动 Iscsitarget 服务了，启动或关闭 Iscsitarget 服务的命令如下： [root@iscsi-target iscsi]# service iscsi-target~~~~~~~Usage: /etc/init.d/iscsi-target {start|stop|restart|condrestart|status} 如果要让 iscsi-target 服务开机自动运行，需执行如下操作： [root@iscsi-target iscsi]#chkconfig --level 35 iscsi-target on 到此为止， iscsitarget 安装完成。

**二、配置一个简单的** **iSCSI target** Enterprise Target 的主配置文件为 /etc/iet/ietd.conf ，此文件中的选项默认全部被注释掉了，有需要用到这些选项时，再将注释去掉即可。 ~ 打开 ietd.conf 文件，首先找到类似如下行： #Target iqn.2001-04.com.example:storage.disk2.sys1.xyz 此选项表示该 iSCSI Target 的命名，先将前面的 &quot;#&quot; 号去掉， Target 的命名在同一子网内应该是唯一的，标准命名方式为： iqn.yyyy-mm.&lt;reversed domain name&gt;[:identifier] 其中： ? ：表示 &quot;iSCSI Qualified Name&quot; ，简称 iqn 。 ? ：表示年份 - 月份。这里是 2001-04 。 ?domain name ：表示倒过来的域名，这里是 com.example 。 ? ：表示识别代码，这里是 storage.disk2.sys1.xyz 。 接下来，就是要设定 LUN （ Logical Unit Number ），找到类似如下行： #Lun 0 Path=/dev/sdb,Type=fileio,ScsiId=xyz,ScsiSN=xyz 将前面的 &quot;#&quot; 号去掉， &quot;Lun 0 Path=/dev/sdb&quot; 表示块设备号为 0 ，映射的磁盘为 /dev/sdb ， &quot;Type&quot; 值 fileio 是默认的，可以用于磁盘、 file 和 LVM ，这里设定的是 &quot;fileio&quot; ，主要用来对一个磁盘进行存储共享。读者可以根据自己情况将 Path 改为需要共享的存储分区的设备标识。这里假定共享的设备标识为 /dev/sdb 。 至此，一个简单的 iSCSI Target 已经配置完毕了，最后启动 iscsi-target 服务： [root@iscsi-target iscsi]# service iscsi-target start

**三、在** **windows** **上配置** **iSCSI Initiator** ~ 下面的操作是在 Initiator 的 windows 主机上进行，即 IP 为 192.168.12.136 主机。 微软对 iSCSI Initiator 的支持相当完备，读者可以免费从微软网站获得 iSCSI Initiator 软件，网址是 [\\t &quot;_blank&quot;](http://blog.chinaunix.net/link.php?url=http://www.microsoft.com%2FWindowsServer2003%2Ftechnologies%2Fstorage%2Fiscsi%2Fdefault.mspx)

### FC SAN {#fc-san}

### FCoE SAN {#fcoe-san}

FCoE， Fibre Channel over Ethernet

### Solution {#solution}

#### openfiler {#openfiler}

[http://www.openfiler.com/](http://www.openfiler.com/)

[http://openfiler.org.cn/](http://openfiler.org.cn/)

Openfiler 能把标准x86/64架构的系统变成一个强大的NAS、SAN存储和IP存储网关，为管理员提供一个强大的管理平台，并能能应付未来的存储需求。依赖如VMware，Virtual Iron和Xen服务器虚拟化技术，Openfiler也可部署为一个虚拟机实例。

Openfiler这种灵活高效的部署方式，确保存储管理员能够在一个或多个网络存储环境下使系统的性能和存储资源得到最佳的利用和分配。

Openfiler的主要性能和优点：

　　● 可靠性　　- Openfiler可以支持软件和硬件的RAID，能监测和预警，并且可以做卷的快照和快速恢复。

　　● 高可用性　- Openfiler支持主动或被动的高可用性集群、多路径存储（MPIO）、块级别的复制。

　　● 性能　　　- 及时更新的Linux内核支持最新的CPU、网络和存储硬件。

　　● 可伸缩性　-文件系统可扩展性最高可超出60TB，并能使文件系统大小可以在线的增长

#### FreeNAS {#freenas}

FreeNAS 是一份基于FreeBSD的小型操作系统，它提供免费的网络附加存储（NAS）服务（CIFS、FTP、NFS）。 FreeNAS 8.0 基于 FreeBSD 8.2 开发。 发行说明： [http://sourceforge.net/mailarchive/message.php?msg_id=27441240](http://sourceforge.net/mailarchive/message.php?msg_id=27441240) 下载地址：FreeNAS-8.0-RELEASE-i386.iso (103MB),FreeNAS-8.0-RELEASE-amd64.iso (105MB)....

### HBA {#hba}

1 、关于HBA

HBA的全称为Host Bus Adapter，即主机总线适配器。

a、总线适配器是个什么东西呢?

我们首先要了解一下主机的结构，一台计算机内部多半由两条总线串在起来(当然实际情况会有不同，这里只讨论常见的，简单的情况)，一条总线叫系统总线，一条叫I/O总线。系统总线上接了CPU，MEmory，cache什么的，I/O总线上接的就是外围设备，现如今最常见的就是PCI总线了。这两条总线之间用桥接的芯片或者说电路连接起来。举个形象的例子，就好比一个城市里，有两条主干道，一条属于行政区，一条属于商业区，中间有个环岛，将两条主干道连接到了一起，系统总线就好比行政区里的主干道，而I/O总线就好比商业区的主干道。系统总线和I/O总线的带宽的单位都是以Gbyte来记，但是显而易见的是，行政区的主干道和商业区的主干道相比的话，前者肯定更&quot;核心&quot;，更宽，更顺畅，设计的要求也高。

我们知道，在向公仆部门要求服务的时候，是要有一些接口的部门和程序的，而桥接芯片的作用就是连接和协调两条总线的工作的。

虽然I/O总线的速度和系统总线的带宽相比要低很多，但是好歹也是以G来计量的，而我们知道外围设备的速度，往往只有几百兆，甚至几十k而已，怎么协调工作呢?好比卖煎饼果子摊子不能直接戳到城市主干道上，怎么办?好办，在主干道边上开个2000平米的小吃城，把摊子都收进去好了。那么主机总线适配器的作用也就是这个，我们就是要把外设组织起来，连接到I/O总线上去!HBA就是指Host和I/O BUS直接的一个适配器，也好比一个水管工常说的&quot;双通&quot;。

b、常见的HBA有哪些呢?

比如显卡，网卡，scsi卡，1394卡等等。我要拿出来说的就是FCHBA和ATA&amp;IDE。我们通常说的什么Emulex的LP9002，什么Qlogic的QLA2340都是FCHBA卡，就是将Fibre Channel的设备和IO总线连接起来的适配器。ATA也是一种适配器技术，我们PC主板上的ATA接口，就是一个磁盘适配器的对外接口，要强调的就是，ATA说的是适配器技术，IDE是说得存储外设技术，比如我们可以说IDE硬盘，IDE光驱，说ATA接口，但是说IDE接口，ATA硬盘就不时那么合适了，虽然很多情况下，大家都习惯把他们混在一起说。

描述HBA的时候，有几个主要的规范要说一下

&gt; 一个承上，就是说，HBA和IOBUS怎么连，我们经常说的PCI接口卡，就是指这个HBA卡是要插在PCI BUS上的PCI slot上的，但是现在的计算机上，不仅仅只有PCI总线而已，大家碰到的时候留意。

&gt;一个启下，就是说HBA要和外设怎么连，这样的规范就很多了。

&gt;再说HBA本身，比如带宽，比如运行机制(protocol等)，独立处理能力等等

Tips：有时候我们看到的一块卡，看到的实际是一个物理的卡，有的时候实际上是多个Adapter，好比一家机构，挂多个牌子，有的时候，一块卡有两条通道，好比一家公司，有两套人马。

### Lun {#lun}

2 、关于LUN

a、lun的概念

lun的全称是logical unit number，也就是逻辑单元号。我们知道scsi总线上可挂接的设备数量是有限的，一般为6个或者15个，我们可以用target ID(也有称为scsi id的)来描述这些设备，设备只要一加入系统，就有一个代号，我们在区别设备的时候,只要说几号几号就ok了。

而实际上我们需要用来描述的对象，是远远超过该数字的，于是我们引进了lun的概念，也就是说lun id的作用就是扩充了target id。每个target下都可以有多个lun device，我们通常简称lun device为lun，这样就可以说每个设备的描述就有原来的target x变成target x lun y了,那么显而易见的,我们描述设备的能力增强了.就好比,以前你给别人邮寄东西,写地址的时候,可以写:

xx市人民大街54号 xxx(收)

但是自从高楼大厦越来越多,你不得不这么写:

xx市人民大街54号xx大厦518室 xxx (收)

所以我们可以总结一下,lun就是我们为了使用和描述更多设备及对象而引进的一个方法而已,一点也没什么特别的地方.

b、lun是什么东西?

lun id不等于某个设备,只是个号码而已,不代表任何实体属性,在我们的实际环境里,我们碰到的lun可能是磁盘空间,可能是磁带机,或者是media changer等等.

lun的神秘之处(相对于一些新手来说)在于，它很多时候不是什么可见的实体，而是一些虚拟的对象。比如一个阵列柜，主机那边看作是一个target device，那为了某些特殊需要，我们要将磁盘阵列柜的磁盘空间划分成若干个小的单元给主机来用，于是就产生了一些什么逻辑驱动器的说法，也就是比target device级别更低的逻辑对象，我们习惯于把这些更小的磁盘资源称之为lun0,lun1,lun2....什么的。而操作系统的机制使然，操作系统识别的最小存储对象级别就是lun device，这是一个逻辑对象，所以很多时候被称之为logical device。

有人说，我的windows里，就认到一个磁盘呀，没看到什么lun的说法，是不是lun=physical disk呢?回答是否定的，只要你注意，磁盘的属性里就可以看到有一个lun的值，只是因为你的disk没有被划分为多个存储资源对象，而将整个磁盘当作一个lun来用，lun id默认为零，如此而已。

我们曾经碰到过这样的问题，比如有人问，我们有一个磁盘阵列，连到了两个主机上，我们划分了一个lun给两个主机认到，然后我们想，先在操作系统将磁盘分为两个区，让两个主机分别使用两个分区，然后再出现某一台主机宕机之后，使用集群软件将该分区切换到另外一个主机上去，这样可行吗?答案也是否定的，集群软件操作的磁盘单元是lun，而不是分区，所以该操作是不可行的。当然，在一些环境，一般也是一些要求比较低的环境，可以在多个主机上挂载不同的磁盘分区，但是这种情况下，实际上是没有涉及到磁盘的切换的，所以在一些高要求的环境里，这种情况根本就不允许存在。

还要说明的地方是，在有些厂商和有些产品的概念里，lun id被绑定到了具体的device上，比如ibm的一些带库，整个带库只有一个target id，然后changer,tape drive被分别分配为lun0,lun1,lun2.....，但是我们要注意到，这只是产品做了特别设计，也是少数情况。

c、存储和主机的电气独立时代的lun的概念

还有很多新手总是把阵列里面的磁盘和主机的内部磁盘的一些概念搞混淆了。

在磁盘阵列和磁带库大行其道的时代，存储越来越智能化，越来越像一个独立的机器，实际上存储和主机的电气独立本来就是一个必然趋势，俗话说得好，儿大要分家嘛。在存储越来越重要的时代，存储要自立门户是必然的事。

如果我们把存储当作一个独立的主机来看，理解起来就很简单了。我们说到lun的概念的时候，我们就要将分为两个层面。一个层面就是在阵列这个机器的os识别到的范围，一个层面就是服务器的os识别到的范围。这两个层面是相对独立的，因为如果我们把存储当作一个主机来看，那么它自然有自己的device，target，lun之说，而服务器也有自己的device,target,lun之说;另外一方面，这两个层面又是相互关联的，一个阵列的控制系统，大多都有虚拟化的功能，阵列想让主机看到什么样的东西，主机才能看到相应的东西。当然，服务器识别到的最小的存储资源，就是lun级别的。那么主机的HBA卡看到的存储上的存储资源就靠主要两个东西来定位，一个就是存储系统的控制器(target)，一个就是lun id，这个lun是由存储的控制系统给定的，是存储系统的某部分存储资源。

d、lun masking，lun mapping

我们有了独立的磁盘阵列用了之后，服务器只要看到存储的控制系统，就有可能使用磁盘阵列的磁盘资源，但是磁盘阵列不可能只为某一个服务器来使用，所以他必须管制主机使用某部分磁盘资源。这个管制分为两个部分：一部分就是lun mapping,类似于绿色通道，就是保证服务器能看到某部分存储资源,一部分就是lun masking，类似于警戒线，就是保证服务器只可访问给它分配的存储资源，而没分配给服务器的资源，就不要染指了。

实现lun masking和lun mapping有三种方法：一个是基于存储控制系统来设置，一个是基于存储交换系统来设置，一个是基于服务器os来设置。

基于存储控制系统得设置，是比较常见的设置，比如很多磁盘阵列的控制系统，本身就能设置lun被某服务器看到。比如FastT的partition功能。

基于存储交换系统的设置，也是一种常用的方法，比如常说的zoning。

基于服务器os的设置，比较少采用，一般采用安装某些操作系统上安装某些软件来实现，因为这个方法全靠服务器自觉，所以比较少用，呵呵。

e、lun的multi-path

现在，存储网络越来越发达了，一个lun有多条通路可以访问也不是新鲜事了。

服务器使用多个HBA连接到存储网络，存储网络又可能是由多个交换设备组成，而存储系统又可能有多个控制器和链路，lun到服务器的存储网络链路又可能存在着多条不同的逻辑链路。那么，必然的，同一个physical lun在服务器上必然被识别为多个设备。因为os区别设备无非用的是总线，target id，lun id来，只要号码不同，就认为是不同的设备。

由于上面的情况，多路径管理软件应运而生了，比如emc的powerpath，这个软件的作用就是让操作系统知道那些操作系统识别到lun实际上是一个真正的physical lun，具体的做法，就是生成一个特别的设备文件，操作系统操作这个特殊的设备文件。而我们知道，设备文件+driver+firmware的一个作用，就是告诉操作系统该怎么使用这个设备。那么就是说，多路径管理软件从driver和设备文件着手，告诉了操作系统怎么来处理这些身份复杂的lun。

### IBM {#ibm}

V7000 可以虚拟化 SAN 环境下所有异构磁盘阵列，形成一个融合的、统一的存储池。

SAN Volume Controller

（缩写为

SVC

），

SAN

控制器，是存储业界又一次崭新的突破，就

像存储历史上的

RAID

，主机系统的存储管理体系和虚拟磁带技术，这些重要的发明均源自

IBM

。

SVC

是整个

SAN

网络的控制器，它将整个

SAN

中的各种存储设备整合成一个巨大的存储

池，充分利用存储资源和按需分配存储空间、性能和功能。而传统的

SAN

网络中，每种存储系

统都自成一体，就像一个个独立的孤岛，无法构成一片统一的大陆。

### EMC {#emc}

[https://community.emc.com/docs/DOC-30566](https://community.emc.com/docs/DOC-30566)

EMC VPLEX是一款真正的虚拟化的存储平台，实现多站点，异构存储整合，统一管理。VPLEX架构的亮点是Active/Active、全冗余、分布式缓存，任意地点访问，双活数据中心等等。本文整理的关于VPLEX的架构的16个问题，从简入深地帮助读者了解实现存储虚拟化的基石 - VPLEX架构。

Q1：EMC VPLEX是什么？

A1：VPLEX是一款分布式、全冗余的存储硬件产品，用来对现有数据中心中已有或者边缘存储资源（EMC或者第三方存储阵列）提供集成的访问与扩展的平台。简单来说，就是整和EMC和非EMC存储，提供跨地域的单点数据访问与数据迁移。

Q2：VPLEX可以解决什么问题？

A2：VPLEX解决的问题有两点：

   从异地数据中心同时访问同一个存储设备，典型的案例就是配合Oracle RAC实现双活数据中心。

   规划与实现数据中心内或者跨数据中心间的数据迁移。比如将数据通过VPLEX从一个存储阵列（同厂商同类型，或者不同厂商不同类型的存储阵列）迁移到另外一个、将应用从一个数据中心迁移到另外一个数据中心。

Q3：VPLEX有什么特别之处？

A3：VPLEX主要特别之处有三点：

   VPLEX组成的集群可以方便的横向（增加集群）与纵向扩展（添加引擎）。

   分布式全局缓存提供分布式数据访问。

   支持长距离的异步传输和（VPLEX Geo版本）多集群架构。

Q4：VPLEX中硬件层面包含哪些主要组件？

A4：VPLEX的工作单元叫做Director，和EMC自家的Symmetrix VMAX存储阵列类似。 两个Active/Active Director组成一个Engine，通过VPLEX Cluster，由不同数量的VPLEX Cluster结合不同的部署位置组成VPLEX的三种解决方案VPLEX Local、VPLEX Metro和VPLEX Geo。

Q5：VPLEX Engine硬件VS2和VS1有什么区别？

A5：VPLEX目前为止推出两款硬件型号，VS1和VS2。VS1和VS2都是用2.4 GHz的Xeon CPU。区别在于VS2的Engine相比VS1引擎在硬件规格上的差别主要体现在VS2使用了PCI Express V2，前者为PCI Express V1，VS2的吞吐量提升了1.5倍。实现Director间通讯的网络方面，VS2也从VS1的4GB提升到8GB，以提供内部通讯更大的带宽。布局方面，VS2也改为垂直布局，相比VS1所占用的空间更小。下面两个表和两张张图，对比VS1和VS2的区别：

VS1硬件规格引擎前后视图

VPLEX16-1.png

VS2硬件规格引擎前后视图：

VPLEX16-2.png

Q6：VPLEX用得什么操作系统？

A6：VPLEX的操作系统名叫GeoSynchrony，最新版本是5.2。VPLEX的主要功能Accessanywhere、卷管理、分布式缓存等等都由这个操作系统完成。

Q7 VPLEX硬件本身有安装物理磁盘存放数据吗？

A7：没有，只有一个SSD用来安装VPLEX的操作系统，实际的数据都存放在后端连接的存储阵列中。

Q8：VPLEX各引擎Director之间如何进行通讯？

A8：VPLEX各引擎中的Director通过光纤交换机进行通讯与数据传输。用的是Connectrix DS-330B的交换机，该交换只能用作VPLEX内部通讯使用。

Q9：VPLEX Cluster是什么？

A9：VPLEX Cluster是指得由1，2或4个VPLEX引擎、加上VPLEX的Management Server、电源与后备电源所组成，物理上全部安装在一个机柜里面的部署单元。VPLEX Local方案中包含一个VPLEX Cluster。而VPLEX Metro和Geo则包含两个VPLEX Cluster。

Q10：VPLEX Local、Metro、Geo三种解决方案有什么区别？

A10：VPLEX Local为单个数据中心打造。VPLEX Metro可以在同步的距离内连接2 个VPLEX集群，在它们之间移动或共享数据。VPLEX Geo则是在异步的距离内连接两个VPLEX集群。VPLEX Local允许在混合平台内镜像存储，而无需主机提供资源和分配虚拟存储设备。 VPLEX Metro与服务器虚拟化相结合，能实现透明地、跨地域的、移动虚拟机及其数据。 VPLEX Metro还允许在同一地点内和跨地点地镜像卷和分布数据。 VPLEX Geo利用Accessanywhere提供支持异步距离的范围可达到 2个站点之间相距超过100公里的能力。引用自：学习存储虚拟化--VPLEX之路

VPLEX16-3.png

Q11：VPLEX有哪些主要子系统？

A11：如果从前至后分，VPLEX有以下几种子系统：

   后端Back-End Storage Volume，VPLEX中的Storage Volume就是VPLEX后端连接的存储阵列所展示给VPLEX的Volume，它可以来自EMC Symmetrix、VNX或者其他第三方存储。

   磁盘虚拟化 Virtual Volume，在VPLEX访问到后端阵列的Volume以后，会将Volume切割成Extent，然后以这个单位再组成的Device就叫做Virtual Volume。

   前端Frond-End Storage View，Storage View的作用就是一个访问控制机制，它和VMAX里面的Masking View工作机制是一样的，把HBA、VPLEX FE Port、Virtual Volume组成映射关系，起到访问控制的作用。

   分布式缓存：Distributed Cache Coherence作为实现分布式工作的核心组件，它通过共享的Engine Cache Coherence Directory来控制不同Director间的I/O流和数据一致性。

VPLEX16-4.png

Q12\. 用户通过何种方式来管理VPLEX？

A12：VPLEX用户可以通过VPLEX Management Console对VPLEX进行管理，VPLEX Management Console同时提供CLI和GUI的用户界面。

Q13：主机访问VPLEX支持多路径吗？

A13：支持，主机可以使用PowerPath等多路径连接到不同的引擎的前端口实现负载均衡和冗余。

Q14：VPLEX如何支持双活数据中心？

A14：VPLEX的Accessanywhere功能提供跨站点的数据访问。而实现应用端的双活，需要配置特定的集群软件才能完成，例如配合Oracle RAC。EMC有相关的白皮书分享，参考：【中文白皮书】利用EMC VPLEX Metro拓展Oracle Real Application Clusters (RAC)的最佳实践

VPLEX16-5.png

Q15：上图中VPLEX Witness的作用是什么？

A15：VPLEX Witness是在GeoSynchrony 5.0以后才推出，是针对Oracle RAC部署中必需组件。VPLEX Witness通过IP 网络连接到两个VPLEX Metro Cluster，将信息进行协调，使得Cluster间的信息得以同步，并在发生Cluster间故障的时候，自动延续对应站点上数据读写。如果没有VPLEX Witness时，但两个VPLEX Cluster失去通讯，在双活的情况下数据一致性就很难保证。VPLEX Witness会动态地自动处理读写活动，使得在VPLEX站点通讯故障回复之前保证数据的一致性。

Q16：VPLEX有没有实际的实施案例与其他资料供参考？

A16：VPLEX已经在各行各业企业中有了实际的装机与实施案例，具体内容参考：VPLEX成功案例

视频资料VPLEX，你的明智之选。介绍了企业在迁移存储阵列过程中面临的挑战，以及VPLEX是如何实现简化迁移过程、消除停机时间、降低迁移风险等目标