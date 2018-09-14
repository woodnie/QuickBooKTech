## HP OpenView OmniBack II {#hp-openview-omniback-ii}

[http://www8.hp.com/cn/zh/software-solutions/software.html?compURI=1175640#tab=TAB3](http://www8.hp.com/cn/zh/software-solutions/software.html?compURI=1175640)

OminiBack=Dat Protector

Data Protector 架构

Cell Manager

Cell Manager 是单元中的主系统。Cell Manager：

* 从中央点管理单元

* 包含IDB（ **内部数据库** 包含备份详细信息（如备份持续时间、介质ID 和会话ID）

* 运行核心Data Protector 软件

* 运行可启动和停止备份及恢复会话并将会话信息写入IDB 的会话管理器

要备份的系统

要备份的客户机系统必须安装了Data Protector 磁带客户机（DA），也称为 **备份代理** 。

要备份联机数据库集成，请安装 **应用程序代理** 。

磁带客户机会从系统上的磁盘中读取数据或将数据写入磁盘，并将数据发送到介质代理或从介质代理接收数据。磁带客户机也安装在Cell Manager 上，因此您也可以在Cell Manager、Data Protector 配置和IDB 上备份数据。

带备份设备的系统

连接有备份设备的客户机系统必须安装了Data Protector **介质代理** （MA）。这样的客户机系统也称为 **驱动器服务器** 。备份设备不仅可以与Cell Manager 相连，也可以与任何系统相连接。

带用户界面的系统

您可以从安装了Data Protector 图形用户界面（GUI）的任何系统通过网络管理Data Protector。因此，您可以在从桌面系统管理Data Protector 的同时在机房中使用Cell Manager 系统。

Installation Server

**Installation Server** 是特定架构下的Data Protector 软件包存储库。默认情况下，Cell Manager 也可视为Installation Server。混合环境需要至少两个Installation Server：一个用于UNIX 系统，一个用于Windows 系统。

日志文件的位置

大多数 Data Protector 日志文件位于：

Windows Vista、Windows 7 和 Windows Server 2008：&lt;Data_Protector_program_data&gt;\log

其他 Windows 系统：&lt;Data_Protector_home&gt;\log

HP-UX、Solaris、Linux：/var/opt/omni/log 和 /var/opt/omni/server/log

其他 UNIX 系统和 Mac OS X 系统：/usr/omni/log

Novell NetWare：SYS:\USR\OMNI\LOG

全局选项

全局选项影响整个 Data Protector 单元，并涵盖 Data Protector 的各个方面，例如超时和限制。全局选项文件中描述了所有全局选项，可以通过编辑此文件来自定义 Data Protector。

全局选项文件位于 Cell Manager 上：

Windows Server 2008：&lt;Data_Protector_program_data&gt;\Config\Server\Options\global

其他 Windows 系统：&lt;Data_Protector_home&gt;\Config\Server\Options\global

UNIX 系统：/etc/opt/omni/server/options/global

要设置全局选项，请编辑全局文件。通过删除&quot;#&quot;标记取消注释所需选项的行，并设置所需的值。

#### GUI {#gui}

Clients

Users

admin

operator

user

Devices &amp; Media

**Environment:**

Devices:Configures and manages backup devices

_CSCHP88-LTO:_

PRNHP03-DLT:

Drives:Physical drives of library

Slots:Physical slots of library

Media:Configures and manages media and media pools

1.poor 表示该磁带在策略里已经认为不可靠，通常是使用时间，或者重复使用次数超购限制

如果还想省钱，可以verify，或者重新recycle，大部分还能接着用

Media

Untitled

**如何为备份选择介质**

Data Protector 介质管理自动选择最适合备份的介质。介质选择的基本标准如下：

*不选择状况差的介质进行备份。

*只有在没有状况良好的介质可用时才使用状况中等的介质。

*如果有，则首先使用状况良好的介质。

*始终从指定的池选择介质。当池不包含不受保护的介质时，Data Protector 将访问空闲池（如果已配置）。

此外，介质选择基于以下因素：

**介质分配策略**

可以使用介质分配策略影响如何为备份选择介质。可以指定宽松策略（任何合适的介质都可用于备份），或严格策略（特定介质必须以预定义顺序可用）。

**预分配介质**

可以指定介质池中的介质将用于备份的顺序。此顺序称为预分配列表。

**介质状况**

介质状况也会影响为备份选择的介质。例如，状况良好的介质在状况中等的介质之前用于备份。状况差的介质不用于备份。

只有在标为中等的介质上没有受保护的介质时才会使用这些介质。否则，将发出装载请求，索要空闲介质。

**介质使用**

介质使用策略控制如何将新备份添加到已使用的介质中，并影响为备份选择哪些介质。

可追加的介质必须处于良好状况，包含某些当前受保护的对象并且不得已满。如果有多个设备用于负载均衡，则可追加的概念按设备适用，即每个设备都使用可追加的介质作为会话中的第一个介质。在相同介质上追加数据的备份会话不一定与相同的备份规范有关。

策略可以是：可追加、不可追加或仅对于增量可追加。

**限制**

在 Travan 设备中使用的介质上不能追加备份。

**注意**

如果使用追加功能，并且备份需要多个介质，则只有所使用的第一个介质可以包含来自以前会话的备份数据。随后，Data Protector 将仅使用空的或不受保护的介质。

可以在介质上为某个客户机创建还原链。这些介质将仅包含一个完整备份以及与同一客户机相关的增量备份：

*对于每个具有仅对于增量可追加介质使用策略的客户机配置一个池。

*将一个不同的池与备份规范中的每个客户机相关，或为每个客户机创建一个单独的备份规范。

请注意，偶尔将创建仅包含增量备份的介质。

介质选择因素

分配策略 首先分配未格式化的介质 Data Protector 选择顺序

宽松(OFF ...)

1.预分配列表（如果指定）

2.可追加的（如使用策略中所设置）

3.不受保护的 Data Protector 介质

4.未格式化的介质

5.中等介质

宽松(ON ...)

1.预分配列表（如果指定）

2.可追加的（如使用策略中所设置）

3.未格式化的介质

4.不受保护的 Data Protector 介质

5.中等介质

严格

不适用

1.预分配列表（如果指定）

2.可追加的（如使用策略中所设置）

3.不受保护的 Data Protector 介质

4.中等介质

Appendable

在DP软件中Media Pool的作用是把带库中的多盘磁带组成一个池(pool)，将磁带的容量得以累加，为一个或多个备份任务提供存储空间。Media Pool可自定义一些功能，如磁带重复读写250次或使用36个月后将被定义为Poor状态，DP软件会提示更换新磁带；备份可为追加方式，即一盘磁带如在一个备份完成后，还有剩余空间，那么可提供给下一个备份继续使用等。使用Media Pool的好处：当某一Media Pool要更换磁带时，我们很容易确定磁带的槽位。

基于不同的模式可方便的规划当前磁带存储的内容，更好的利用磁带的空间

Appendable（追加模式）

备份数据在磁带上，当磁带上已有数据，新的备份允许后接在以前备份的数据后。

Non Appendable（非追加模式）

备份数据在磁带上，当磁带上已有数据，新的备份不允许后接在以前备份的数据后，必须在一个新的磁带上开始备份。

Appendable of Incrementals Only

备份数据在磁带上，当磁带上已有数据，新的备份是增量备份就允许后接在以前完全备份的数据后，如果是一个完全备份就必须在一个新的磁带上开始备份。

Allocation Policies

Strict

严格的备份策略要求media pool里的磁带必须先格式化才可使用，一般不推荐使用此策略。

Loose

宽松的备份策略接受任何磁带除了已经标记状态为poor的磁带，推荐使用此策略。

Unformatted media first 当media pool的磁带无空间后，优先使用尚未格式化的磁带，（和loose策略组合使用）。

Use free pool当media pool的磁带无空间后，优先使用free pool（和loose策略组合使用，谨慎使用此功能）。

Untitled

介质池属性 - 分配

介质分配策略定义介质池中访问介质的顺序，以使介质均匀地磨损。包括：

***严格**

*宽松

*首先分配未格式化的介质

*使用空闲池

*将空闲介质移至空闲池

*箱盒支持

--------------------------------------------------------------------------------

介质池属性 - 条件

介质状况因素

介质状况因素定义介质的状态，因此确定介质能够可靠地用于备份的时间长度。例如，备份到旧或磨损的介质更容易产生读/写错误。根据这些因素，Data Protector 将介质的状况从良好改为中等或差。对整个介质池而非每个介质设置状况因素。

重要说明

要使 Data Protector 准确计算介质的状况，请在向介质池添加介质时使用新介质。

注意

如果池使用空闲池选项，则从空闲池继承介质状况因素。

可以选择的两个介质状况因素包括：

*最大重写次数

*有效期(月)

--------------------------------------------------------------------------------

介质池属性 - 使用

介质使用策略控制如何将新备份添加到已使用的介质中。包括：

***可追加**

如果选择此选项，则备份会话使用的第一个介质包含从上一个备份会话备份的数据，因此会使用介质上的剩余空间。如果在同一个备份会话期间需要其他介质，则会使用空的或者取消保护的介质。

如果池中有多个可用的可追加介质，将使用最早写入的介质。

通过此介质使用策略，备份类型（完整或增量备份）可以在介质上以任何顺序组合。

追加介质可以节省介质空间，但降低了操纵介质的灵活性，因为一个介质可能包含来自几个备份会话的数据。

对于文件库不建议使用可追加介质使用策略。此外，如果使用文件库执行对象复制或对象合并，则不支持可追加策略。需要使用不可追加介质使用策略。

***不可追加**

如果选择此选项，则只能将数据从一个备份会话写入此特定介质。尝试将备份会话追加到此介质将导致发出装载请求。您需要响应装载请求。

***仅对于增量可追加**

如果选择此选项并执行增量备份，则备份会话使用的第一个介质包含从上一个备份会话备份的数据，因此会使用介质上的剩余空间。如果在同一个备份会话期间需要其他介质，则会使用空的或者取消保护的介质。

如果池中有多个可用的可追加介质，将使用最早写入的介质。

此介质使用策略将创建包含一个完整备份并且后跟许多增量备份的介质。

--------------------------------------------------------------------------------

Backup

Monitor

Restore

1.Restore Object

1.1File System

host1

       dir1

       dir2

host2

       dir1

       dir2

...

1.2OmniBack II Database

cschp88.sct.ucarb.com

[Datebase[]]

**Source**

Select the files and directories that you want to restore.

Search interval [ ]

**Destination**

Options

Slect options for how you want you data restored and specify any pre-exec and post-exec commands.

**Devices**

View the devices needed for the restore session.

Media

Restore Summary

Untitled

glbck3.nam.dow.com

1.3Disk Image

2.Restore Sessions

Instant Recovery

Reporting

Omniback II Database

Object

Object

Sessions

Usage

#### Tips {#tips}

**5.如何查看当前正在执行的备份任务**

选择Monitor界面，可以看到当前正在执行的所有任务，也可以执行omnistat，看到当前正在执行的所有任务。

**6.如何停止当前正在执行的备份任务**

在Monitor界面，选择该任务，在Actions菜单，选择Abort操作。在命令行，执行omniabort -session &lt;SessionID&gt;

**7.如何查看已经结束的备份任务**

在Internal Database界面，选中Sessions，可以看到所有的备份，用鼠标右键点击一个任务，选择属性，可以看到备份日志。 在命令行，用omnidb -session可以看到所有的备份任务，用omnidb -session &lt;SessionID&gt; -report可以看到备份日志

**16.如何理解mount request的提示**

在备份过程中，如果介质池中已经没有可用的磁带了，则DP软件会自动选择一个不属于任何介质池的带库槽位，并显示Mount Request信息，提示用户放入一盘可用的磁带。在等待客户放磁带的过程中，备份任务一直处于等待状态，它占用的系统资源不会释放。这意味着，如果是数据库备份，则数据库一直处于备份模式，可能导致数据库停机。

如果要改变这种方式，需要修改DP的一个教本，mount.sh/mount.bat，增加下列语句：

/opt/omni/bin/omniabort -session $SESSIONID 2&gt;/dev/null 1&gt;/dev/null

软件的文件结构

/etc/opt/omni  ---DP配置信息

/opt/omni   ---DP执行程序

/var/opt/omni ---DP内部数据库及log信息

DP软件的配置信息存放在Cell Server的 /etc/opt/omni/server目录下:

/etc/opt/omni/server/cell     --- 存放cell server的信息 *

/etc/opt/omni/server/integ/config --- 存放DP与数据库的集成脚本 *

/etc/opt/omni/server/datalists  --- 存放文件系统的部分脚本 *

/etc/opt/omni/server/schedules  --- 存放文件部分的计划时间信息 *

/etc/opt/omni/server/barlists    --- 存放数据库在线部分的脚本  *

/etc/opt/omni/server/barschedules--- 存放数据库在线部分的计划时间信息 *

/etc/opt/omni/server/Users   --- 存放DP中用户配置的信息

DP软件的执行程序存放在 /opt/omni目录下  

* /opt/omni/lbin

* /opt/omni/sbin

* /opt/omni/bin

DP软件内部数据库,使用第三方的Velocis数据库做为其内部数据库，存放在/var/opt/omni/db40目录下，主要包含以下几部分：  

* /var/opt/omni/db40/datafiles/cdb --- 存放DP Internal  Database中Sessions等信息  

* /var/opt/omni/db40/datafiles/mmdb --- 存放DP Device &amp;  Media等信息  

* /var/opt/omni/logs --- 存放DP log，包括debug.log ； media.log ；IS_install.log；license.log；如informix.log等数据库备份信息。   请不要手工修改db40目录下的任何文件，log目录下的信息则有助于诊断问题。

DP软件的后台进程  

3.1 DP软件的自动启动配置  

DP软件安装后，在/etc/rc.config.d目录下会产生一个文件omni，其缺省设置为随主机自动启动。建议不要对其进行修改。  

3.2 DP软件的手工启动方法  

DP软件的手工启动或停止方法为在Cell Manager主机上执行如下命令：  

* /opt/omni/sbin/omnisv -start  --- 手工启动DP进程   或者/sbin/init.d/omni start  

* /opt/omni/sbin/omnisv -stop  --- 手工停止DP进程    或者/sbin/init.d/omni stop  

* /opt/omni/sbin/omnisv -status  --- 观察DP后台进程的状态    

3.3 DP软件的后台进程  观察DP后台进程的状态有如下2种方法：  

* /opt/omni/sbin/omnisv -status 正常状况下应看到如下信息      

ProcName     Status   [PID]  

===============================    

rds      : Active  [888]    

crs      : Active  [792]    

mmd      : Active  [848]    

omniinet : Active  [804]    

Sending of traps disabled.  

===============================  

Status: All Data Protector relevant processes/services up and running.  

* Ps -ef | grep omni正常状况下应看到如下信息  

/opt/omni/lbin/crs

/opt/omni/lbin/rds

/opt/omni/lbin/mmd

#### progress {#progress}

BSM:Data Protector Backup Session Manager ，可控制备份会话。此进程始终在 Cell Manager 系统上运行。连接组件：用户界面（GUI/CLI）；

UMA ： Utility Media Agent ，仅在若干系统之间共享库时需要与 (UMA) 连接。 连接组件 Media Agent （ xMA ）

BMA: 备份 Media Agent1

DBBDA:

VBDA:Disk Agent 客户机

#### TAPE：LTO&amp;DLT&amp;AIT {#tape-lto-dlt-ait}

目前在磁带存储技术上主要应用的技术有三种：LTO（Linear Tape-Open，开放线性磁带）、DLT（Digital Linear Tape，数码线性磁带）和AIT（Advanced Intelligent Tape，先进智能磁带）。这三种技术共同存于市场上已经一段时间了，它们的市场占有率有很大差别，推崇它们的厂商也都有自己完善的解决方案。对于用户的不同需求，这三种技术都有各自的优缺点，了解它们各自的性能特点，将会帮助用户选择到底自己适合使用哪种技术。

      目前解决企业数据保存问题行之有效的方法依然是使用磁带存储设备。磁带设备既是网络存储备份设备的元老，又是网络存储备份设备最有生气的主力军，磁带这种最基本的存储单元，依然会在存储技术突飞猛进的今天，发挥着它巨大的作用。近年来，数据的爆炸性增长给磁带设备带来了更多的需求，也加剧了存储厂商在这一领域的争夺战。存储市场的争夺实际上就是一场技术上的较量。谁掌握了最先进的存储技术，谁的技术最符合用户的需求，谁就掌握了竞争的主动权。

      在存储备份技术发展史上，曾经出现过多种备份技术，但时过境迁，很多当年主打的技术已经被市场慢慢淘汰，取而代之的新技术逐渐占据了市场的主流位置。目前这些主流技术有AIT、DLT和LTO。这三种技术以其各自的优势占据着各自的市场份额。据Gartner Dataquest公布的报告，2001年磁带驱动器市场DLTtape技术占据份额达67%，位列次席的是占据15%份额的LTO技术，而AIT占据大约9%的市场份额。但是未来存储市场的宠儿，必须要进一步由市场来证实，三者都在等待着市场的判决。

LTO探索开放标准

      LTO由IBM、惠普和希捷公司联合建立。LTO有两种格式--Ultrium和Accelis。前者的特点是高容量，后者的特长在于存取速度快。惠普主要研制Ultrium格式的产品，并相信它是未来产品的发展方向。Ultrium采用单轴1/2英寸磁带，非压缩存储容量100GB、传输速率最大20MB/s、压缩后容量可达200GB，而且具有增长的空间（关于IBM和希捷的LTO产品与昆腾SDLT产品的性能对比见后表）。Ultrium结合了线性多通道双向磁带格式的优点，基于服务系统、硬件数据压缩、优化的磁道面和高效率纠错技术，以提高磁带的能力和性能，广泛应用于高端服务器、大型数据库等领域。

LTO自称是开放磁带系统。从理论上讲，这一开放式系统将促使标准化介质的生成，并使该介质能够由一个供应商的系统写入，由另一供应商的驱动器续写，并且由其它制造商的第三方系统成功读出。如果这一理念能够得到实施，那么无疑将成为一大创举。但令人遗憾的是，以LTO产品为代表的具体实施情况目前在开放性方面还存在着显著缺陷。

      LTO技术就其本质而言属于线性螺旋技术，它在各个方面均证明自己是当前该种类技术最好的一种应用方式。首先，它能够保证更多数量的并行信道。第一代的开放线性磁带技术可同时支持8条信道，而以后的版本将提供16条信道。与此相比较，多数的线性螺旋应用技术最多只能提供4条信道。

      LTO技术的开发还利用了当今最为先进的伺服以及磁头技术，这些技术保证了高密磁轨的精确度。磁带的轨道数越多，覆盖相邻轨道数据的危险性就越大。LTO技术将磁轨通过伺服监视器进行编排，并对磁带上的磁头进行控制，从而能够确保精确度并避免发生覆盖现象。另外，LTO技术还可提供超过当前任何线性磁带技术性能的实密度（100MB/平方英寸）高能录制。这一高线性密度通过增强的逻辑格式予以支持，它包括对用户数据的多条数据轨道进行紧密跟踪录制，而这些用户数据又通过多轨道运行的纠错编码来加以保护，这一保护措施还可应付偶发性错误率突然上升的情况。

      有专家认为：LTO磁带似乎是20世纪90年代末的一大创举，供应商联盟可借此提供可交换性产品以避免局限于单个供应商。但是，惠普、IBM和希捷等命名相似的产品已显现出各自设计上的差异，而这些偏差对LTO技术的&quot;开放式&quot;价值定位来说无疑是致命的打击。对于LTO不利的另一因素是，惠普、IBM和希捷也正在DLT标准方面展开激烈的竞争。另外，LTO业务也不是这三家公司的核心所在。在惠普和IBM强调软件/服务以及当前企业集中于关键能力的趋势中，一时还难以判断谁将驻守LTO领域。由于LTO标准的改进需要三大相互竞争的制造商的共同参与，所以其中在进行必要的研发和产品开发工作中速度最慢的一方将决定整个联盟的进度。

      当前LTO整体结构的彻底改造是无法避免的。任何公司的研发力量都是极其宝贵的资源，但在如何最有效利用这一资源方面则存在较大分歧。这些资源应该用于全新的打破常规的产品以改变行业局面，还是应该把这些有限的资源用于升级改进现有产品以获得近期的市场竞争优势？磁带市场的现况加剧了这一两难境地，三大制造商虽然名义上致力于LTO标准，但实际上却在彼此之间同时与其它存储技术标准之间展开激烈的竞争。或许它们应该将宝贵的研发资源集中在一起以提升产品的整体性能，而不是将其用于开发区别极小的产品，从而在三个供应商之间彼此竞争。

      无论如何，由于重量级厂商的参与，LTO格式已经成为磁带存储领域的一支主力军，其市场份额不断增长。第三方的磁带机生产厂商StorageTek认为，LTO市场份额增长很快，但实际上是抢了原有的DLT及Super DLT的市场。不可否认，LTO将是客户看重的技术。另一家磁带机生产厂商ADIC认为，目前基于LTO的磁带库在线形存储、集成度与扩展性方面占有一定的优势。

AIT寻求突破

      AIT是指先进智能磁带。AIT虽然属于存储技术的新军，但是由于具有螺旋扫描、金属蒸发带等先进技术，前景显得更加美好。AIT不仅在结构设计上相当突出，其磁带本身也相当特殊。在存储介质上，AIT的数据保护性能比较突出。不像其它平常金属物质的磁带， AIT所使用的AME（Advanced Metal　Evaporated）磁带不含有非磁性粘着物质，可避免磁头阻塞或造成机器的污染。AIT 磁带机因为能提供档案较长的保存期限及读写头的使用周期，所以能让企业用户对他们存储的数据放心。

      AIT的特点之一是MIC（Merry-In-Cassette）卡匣设计及磁带纪录方式。MIC是将 64Kb的快闪记忆芯片设计在磁带匣上，其可储存tape log，search map及用户自订的数据，所以不需读完全部的磁带即可找到档案。同时AIT纪录数据的方式是使用螺旋式的扫描方法，数据磁道是以一个角度写在8mm宽的磁带边缘。

AIT已经发展到目前的AIT-3，与DLT和LTO不同的是，后二者属于线性记录介质，而AIT是螺旋记录介质。线性记录格式发展时间长，进入中国市场也较早，市场占有率较高，不过采用螺旋记录格式的磁带机由于具有体积小巧、可靠性高、数据传输速度快、磁头和磁带寿命长等特点，近年来异军突起，迅速抢占了大量市场份额，逐步得到了用户的认可。在采用螺旋扫描技术的磁带机中，只有磁鼓是高速旋转的，其他部件（如磁带、伺服机构等）都是低速运转的。螺旋扫描系统控制磁带以一个较低的速度经过高速旋转的大尺寸磁鼓，磁鼓上的超金属磁头（HyperMetal）在磁带上形成密度很高的记录轨道。磁鼓的高速旋转会在磁带与磁鼓之间产生十分细小稳定的气流，可以保护磁带不受损伤。磁鼓相对于底座轻微的倾斜缩小了磁迹间距，使得高速的数据传输和高密度的记录成为简单的技术动作。这样的结构紧凑合理、易于设计和维护，在相同材料下，较低的磁带走速减少了由于张力过大带来的磁带寿命的减少，所以采用螺旋扫描的方式能使材料寿命延长。

     虽然目前了解AIT的用户数量没有了解DLT和LTO的多，但是具有优势的技术总会得到更多的市场青睐。目前开发AIT技术的索尼公司和专注在AIT技术上开发产品的Spectra Logic公司都在大力的推广采用AIT的产品。越来越多的厂商参与到AIT这个阵营中，AIT领军磁带存储市场的明天指日可待。

DLT稳中求胜

      DLT采用线性记录技术，其特点是大容量、高速度。DLT的发展是要解决较早的QIC（1/4英寸盒带）的问题。DLT也用来替换旧式的4mm和新的8mm磁带格式。在接受这些不同的磁带备份技术时，数据容量、速率和可靠性是关键的考虑因素。DLT把4mm或者8mm的速率提升了3到4倍，存储容量方面也增加了4倍。它的对手--螺旋扫描虽然能提供更高的密度，但又带来媒体老化时传动机构调整和数据完整性的问题。当系统频繁使用时，磁带媒体的性能和传动可靠性是至关重要的因素。任何对磁带系统结构的简化都可降低故障率。DLT利用直线盘形的记录原理，比较不容易出现磁头故障和磁带路径的调整偏差，因而得到推广。

      DLT技术采用单轴1/2英寸磁带仓，以纵向曲线型记录法为基础。DLT产品主要应用于中、高端服务器市场与磁带库应用系统，市场占有率增长很快。DLT以纵向曲线型记录法在磁带上进行记录，具有大容量、高速度的特点。它也是少数使用单轴1/2英寸磁带仓的磁带机产品，主要应用于中、高端数据库存储和磁带库中。目前DLT磁带机的容量从10GB到80GB不等，非压缩存储数据传送速度为1.25MB/s至10MB/s（压缩后可使容量和存储速度提升约一倍）。未来DLT存储容量会达到160GB/320GB，在高速存储速率和容量方面，DLT占有优势。据昆腾公司称：到2006～2007年，SDLT的容量将达到每一盘磁带一个TB，速度达到每秒100兆。StorageTek也认为，在未来的几年内，磁带的容量会更大，可达到TB级。目前经昆腾测试，现有的技术使得500GB的容量已经可以很容易达到，这个技术已经非常成熟。实际上SDLT并不是昆腾一家去做，昆腾也授权一些其他公司在生产或设计SDLT，比如腾保公司等。

      Super DLT（SDLT）技术是昆腾公司2001年推出的格式，它在DLT技术基础上结合新型磁带记录技术，使用激光导引磁记录（LGMR）技术，通过增加磁带表面的记录磁道数使记录容量增加。目前SDLT的容量为160GB，近3倍于DLT磁带系列产品，传输速率为11MB/s，是DLT的2倍。SDLT虽然对DLT磁带做了很多改进，但仍然可以读取DLT磁带，与保有量很大的DLT 4000、7000和8000驱动器有着良好的向下兼容性。高级金属粉末（AMP）介质和其他先进技术的应用使SDLT磁带存储密度相当高，用户单位存储成本也随之降低。SDLT磁带驱动器目前受到主流ISV的广泛支持，是具有发展潜力的高性能磁带机。未来SDLT存储容量会达到320GB/640GB。

      结束语通过上面介绍，我们建议，如果企业需要很高的扩展性，需要多家不同的厂商产品很好的兼容，LTO是首选；如果企业存储数据读写频繁，DLT由于利用直线盘形的记录原理，不容易出现磁头故障和磁带路径的调整偏差，所以是很好的选择；如果企业数据需要保存很长时间，并且需要快速搜索数据，AIT是不二之选。

#### Reference {#reference}

DP 日常维护

[http://wenku.baidu.com/view/141bde80d4d8d15abe234e1c.html](http://wenku.baidu.com/view/141bde80d4d8d15abe234e1c.html)

#### Install DataProtect 6 {#install-dataprotect-6}

xinetd

omnisetup.sh [-source &lt;directory&gt;] [-server &lt;name&gt;] [-install &lt;component_list&gt;]

./omnisetup.sh -CM -IS

install TS:

uiproxyd：erro 1053:

1.port 5555

2.xinet staus

3\. vi /etc/opt/omni/client/cell_server

4\. cp *.so  /lib64/

2.libstdc

install libstdc++.5.so

compat-libstdc++-33.x86_64