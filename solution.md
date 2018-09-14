# Solution {#solution}

#### MAC绑定IP {#mac-ip}

[1]

在2960交换机中如何进行端口MAC地址绑定，并同时绑定IP与MAC地址？

IP地址与MAC地址的关系： IP地址是根据现在的IPv4标准指定的，不受硬件限制长度4个字节。而 MAC地址却是用网卡的物理地址，保存在网卡的EPROM里面，与硬件有关系，长度为6个字节。

在交换式网络中，交换机维护一张MAC地址表，并根据MAC地址，将数据发送至目的计算机。 为什么要绑定MAC与IP 地址：IP地址的修改非常容易，而MAC地址存储在网卡的EEPROM中，而且网卡的MAC地址是唯一确定的。因此，为了防止内部人员进行非法IP盗用 (例如盗用权限更高人员的IP地址，以获得权限外的信息)，可以将内部网络的IP地址与MAC地址绑定，盗用者即使修改了IP地址，也因MAC地址不匹配而盗用失败:而且由于网卡MAC地址的唯一确定性，可以根据MAC地址查出使用该MAC地址的网卡，进而查出非法盗用者。

在Cisco中有以下三种方案可供选择，方案1和方案2实现的功能是一样的，即在具体的交换机端口上绑定特定的主机的MAC地址（网卡硬件地址），方案3是在具体的交换机端口上同时绑定特定的主机的MAC地址（网卡硬件地址）和IP地址。

1.方案1--基于端口的MAC地址绑定

思科2950交换机为例，登录进入交换机，输入管理口令进入配置模式，敲入命令：

Switch#config terminal

＃进入配置模式

Switch(config)# Interface fastethernet 0/1

＃进入具体端口配置模式

Switch(config-if)#Switchport port-secruity

＃配置端口安全模式

Switch(config-if )switchport port-security mac-address MAC(主机的MAC地址)

＃配置该端口要绑定的主机的MAC地址

Switch(config-if )no switchport port-security mac-address MAC(主机的MAC地址)

＃删除绑定主机的MAC地址

注意：

以上命令设置交换机上某个端口绑定一个具体的MAC地址，这样只有这个主机可以使用网络，如果对该主机的网卡进行了更换或者其他PC机想通过这个端口使用网络都不可用，除非删除或修改该端口上绑定的MAC地址，才能正常使用。

注意：

以上功能适用于思科2950、3550、4500、6500系列交换机

2.方案2--基于MAC地址的扩展访问列表

Switch(config)Mac access-list extended MAC10

＃定义一个MAC地址访问控制列表并且命名该列表名为MAC10

Switch(config)permit host 0009.6bc4.d4bf any

＃定义MAC地址为0009.6bc4.d4bf的主机可以访问任意主机

Switch(config)permit any host 0009.6bc4.d4bf

＃定义所有主机可以访问MAC地址为0009.6bc4.d4bf的主机

Switch(config-if )interface Fa0/20

#进入配置具体端口的模式

Switch(config-if )mac access-group MAC10 in

＃在该端口上应用名为MAC10的访问列表（即前面我们定义的访问策略）

Switch(config)no mac access-list extended MAC10

＃清除名为MAC10的访问列表

此功能与应用一大体相同，但它是基于端口做的MAC地址访问控制列表限制，可以限定特定源MAC地址与目的地址范围。

注意：

以上功能在思科2950、3550、4500、6500系列交换机上可以实现，但是需要注意的是2950、3550需要交换机运行增强的软件镜像（Enhanced Image）。

3.方案3--IP地址的MAC地址绑定

只能将应用1或2与基于IP的访问控制列表组合来使用才能达到IP-MAC 绑定功能。

Switch(config)Mac access-list extended MAC10

＃定义一个MAC地址访问控制列表并且命名该列表名为MAC10

Switch(config)permit host 0009.6bc4.d4bf any

＃定义MAC地址为0009.6bc4.d4bf的主机可以访问任意主机

Switch(config)permit any host 0009.6bc4.d4bf

＃定义所有主机可以访问MAC地址为0009.6bc4.d4bf的主机

Switch(config)Ip access-list extended IP10

＃定义一个IP地址访问控制列表并且命名该列表名为IP10

Switch(config)Permit 192.168.0.1 0.0.0.0 any

＃定义IP地址为192.168.0.1的主机可以访问任意主机

Permit any 192.168.0.1 0.0.0.0

＃定义所有主机可以访问IP地址为192.168.0.1的主机

Switch(config-if )interface Fa0/20

#进入配置具体端口的模式

Switch(config-if )mac access-group MAC10 in

＃在该端口上应用名为MAC10的访问列表（即前面我们定义的访问策略）

Switch(config-if )Ip access-group IP10 in

＃在该端口上应用名为IP10的访问列表（即前面我们定义的访问策略）

Switch(config)no mac access-list extended MAC10

＃清除名为MAC10的访问列表

Switch(config)no Ip access-group IP10 in

＃清除名为IP10的访问列表

上述所提到的应用1是基于主机MAC地址与交换机端口的绑定，方案2是基于MAC地址的访问控制列表，前两种方案所能实现的功能大体一样。如果要做到IP 与 MAC地址的绑定只能按照方案3来实现，可根据需求将方案1或方案2与IP访问控制列表结合起来使用以达到自己想要的效果。

注意：以上功能在思科2950、3550、4500、6500系列交换机上可以实现，但是需要注意的是2950、3550需要交换机运行增强的软件镜像（Enhanced Image）。

后注：从表面上看来，绑定MAC地址和IP地址可以防止内部IP地址被盗用，但实际上由于各层协议以及网卡驱动等实现技术，MAC地址与IP地址的绑定存在很大的缺陷，并不能真正防止内部IP地址被盗用。

[2]

前言：我本来没有想过写关于ARP绑定的文章，坦白的说一句，在你理解ARP工作的原理时，这其实比较简单。只是看到最近论坛很多人在问关于绑定IP和MAC地址的问题，

所以才决定写这个文章，希望能一劳永逸。

作为企业级的路由防火墙，ISA Server并没有提供对于MAC地址的控制功能。不过，你可以使用Windows的命令ARP来实现IP地址和MAC地址的绑定。这篇文章介绍了 Windows下ARP协议工作的原理，以及如何使用ARP命令来静态绑定IP地址和MAC地址。

ISA Server中没有提供对于MAC地址的控制功能，Why？这是因为MAC地址只能在本地网络中使用，当数据包跨越路由器时，数据包中主机的源MAC地址就会被路由器的出站接口的MAC地址所代替，这个时候，使用MAC地址来进行控制就不适用了。所以只要是企业级的硬件或者软件防火墙，都基本没有提供对 MAC地址的控制功能。

不过微软也早就考虑到了这点，在Windows中，如果你安装了TCP/IP网络协议组件，那么你就可以执行命令 ARP。ARP命令的作用是查看本机的ARP缓存、静态绑定IP地址和MAC地址和删除静态绑定项。其实绑定IP地址和MAC地址的本意是为了减少ARP 广播流量，只是可以利用这一功能来控制IP地址的使用。

在这里我还是先简单的描述一下Windows下ARP协议的工作原理。ARP协议（Address Resolve Protocol，地址解析协议）工作在TCP/IP协议的第二层－数据链路层，用于将IP地址转换为网络接口的硬件地址（媒体访问控制地址，即MAC地址）。

无论是任何高层协议的通讯，最终都将转换为数据链路层硬件地址的通讯。

每台主机都具有一个用于缓存MAC地址的ARP缓存列表，你可以使用命令ARP -a或ARP -g来查看当前的ARP缓存列表。此ARP缓存列表是动态更新的，默认情况下，当其中的缓存项超过两分钟没有活动时，此缓存项就会超时被删除。你可以使用 ARP -s来静态绑定IP地址和MAC地址，不过在Windows server 2003和XP以前的Windows系统中，就算你设置了静态MAC地址绑定项，同样会通过接收其他主机的数据包而更新已经绑定的项。

在Windows server 2003和XP中，静态绑定的项不会被动态更新，直到TCP/IP协议终止为止，例如重启计算机

。如果要创建永久的静态MAC地址绑定项，你可以写一个脚本文件来执行ARP静态绑定，然后使用计划任务在启动计算机时执行该脚本即可。

例如A主机的IP地址为192.168.0.1，它现在需要与IP为192.168.0.8的主机（主机B）进行通讯，那么将进行以下动作：

A主机查询自己的ARP缓存列表， 如果发现具有对应于目的IP地址192.168.0.8的MAC地址项，则直接使用此MAC地址项构造并发送以太网数据包，如果没有发现对应的MAC地址项则继续下一步；

A主机发出ARP解析请求广播，目的MAC地址是FF:FF:FF:FF:FF:FF，请求IP为192.168.0.8的主机回复MAC地址；

B主机收到ARP解析请求广播后，回复给A主机一个ARP应答数据包，其中包含自己的IP地址和MAC地址；

A接收到B主机的ARP回复后，将B主机的MAC地址放入自己的ARP缓存列表，然后使用B主机的MAC地址作为目的MAC地址，B主机的IP地址（192.168.0.8）作为目的IP地址， 构造并发送以太网数据包；

如果A主机还要发送数据包给192.168.0.8， 由于在ARP缓存列表中已经具有IP地址192.168.0.8的MAC地址，所以A主机直接使用此MAC地址发送数据包，而不再发送ARP解析请求广播；当此缓存地址项超过两分钟没有活动（没有使用）后，此ARP缓存将超时被删除。

默认情况下ARP缓存的超时时限是两分钟，你可以在注册表中进行修改。可以修改的键值有两个，都位于

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters

修改的键值：

键值1：ArpCacheLife，类型为Dword，单位为秒，默认值为120

键值2：ArpCacheMinReferencedLife，类型为Dword，单位为秒，默认值为600

注意：这些键值默认是不存在的，如果你想修改，必须自行创建；

修改后重启计算机后生效

。

如果ArpCacheLife的值比ArpCacheMinReferencedLife的值大，那么ARP缓存的超时时间设置为ArpCacheLife 的值；如果ArpCacheLife的值不存在或者比ArpCacheMinReferencedLife的值小，那么对于未使用的ARP缓存，超时时间设置为120秒；对于正在使用的ARP缓存，超时时间则设置为ArpCacheMinReferencedLife的值。

下图是我们的试验网络结构，ISA Server作为一个边缘防火墙，内部局域网（192.168.0.0/24）通过ISA Server接入Internet。在这个试验中，我将在ISA Server上绑定内部客户True的IP地址192.168.0.8和MAC地址，这样，当True不在线时，另外一个内部客户Fake就算修改自己的 IP地址为True的IP地址192.168.0.8，也不能通过ISA Server来上网。

各计算机的TCP/IP设置如下，本次试验不涉及DNS解析，各服务器的DNS服务器设置为空，在试验之前已经确认了网络连接工作正常：

ISA 2004 Firewall：

LAN Interface：

IP：192.168.0.1/24

DG：None

MAC：00:03:47:F4:FC:E7

True（将离线）：

IP：192.168.0.8/24

DG：192.168.0.1

MAC：00:0D:60:C3:05:34

Fake（将修改IP地址为192.168.0.8）：

IP：192.168.0.8/24

DG：192.168.0.1

MAC：00:06:D0:06:05:47

首先，我在ISA Server上使用ARP -S来绑定True的IP地址和MAC地址，运行命令：

ARP -s 192.168.0.8 00-0D-60-C3-05-34

然后执行ARP -a来查看ARP缓存列表，结果如下图所示。你可以看到在ARP缓存列表中IP地址192.168.0.8的类型为static，这表明它是静态项。此时，我们在ISA Server上的绑定就成功了。

现在我们在客户机Fake上，将自己的IP地址修改为192.168.0.8，然后Ping ISA Server：

C:\Documents and Settings\admin&gt;ipconfig /all

Windows IP Configuration

Host Name . . . . . . . . . . . . : anonymous

Primary Dns Suffix . . . . . . . :

Node Type . . . . . . . . . . . . : Unknown

IP Routing Enabled. . . . . . . . : No

WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter 本地连接:

Connection-specific DNS Suffix . :

Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

Physical Address. . . . . . . . . : 00-06-D0-06-05-47

Dhcp Enabled. . . . . . . . . . . : No

IP Address. . . . . . . . . . . . : 192.168.0.8

Subnet Mask . . . . . . . . . . . : 255.255.255.0

Default Gateway . . . . . . . . . : 192.168.0.1

DNS Servers . . . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\admin&gt;ping 192.168.0.1 -n 2

Pinging 192.168.0.1 with 32 bytes of data:

Request timed out.

Request timed out.

Ping statistics for 192.168.0.1:

Packets: Sent = 2, Received = 0, Lost = 2 (100% loss),

Ping超时，Why？从Sniffer上捕获的数据包可以更清楚的进行说明：

下图是捕获的数据包，它描述了Fake（192.168.0.8） Ping 192.168.0.1的全部过程：

由于Fake（00:06:D0:06:05:47）没有192.168.0.1的MAC地址，所以Fake发送ARP地址解析请求广播，询问192.168.0.1的MAC地址是什么；

ISA Server（00:03:47:F4:FC:E7）使用ARP应答回复Fake（00:06:D0:06:05:47），告诉Fake自己的IP地址（192.168.0.1）和MAC地址；

获得192.168.0.1的MAC地址后，Fake（192.168.0.8）向192.168.0.1发送PING请求数据包；

192.168.0.1向192.168.0.8回复PING回复数据包；

Fake（192.168.0.8）再次向192.168.0.1发送PING请求数据包；

192.168.0.1再次向192.168.0.8回复PING回复数据包；

这一切看起来没有任何问题？那为什么Fake的Ping会超时呢？

这一切从表明上看是没有任何问题，但是仔细看捕获的数据包的以太网头部，你就会发现问题所在：

首先，我们看第三个数据包，Fake（192.168.0.8）向192.168.0.1发送的Ping请求，如下图所示，Fake以自己的MAC地址为源 MAC地址、192.168.0.1的MAC地址（00:03:47:F4:FC:E7）为目的MAC地址发送数据包，这没有任何问题。

那么看看第四个ISA Server回复的Ping回复数据包呢，源MAC地址是ISA Server的MAC地址（00:03:47:F4:FC:E7），这也没有问题，但是注意看目的MAC地址，00:0D:60:C3:05:34是离线的客户机True的MAC地址。还记得我们在ISA Server上做的IP地址（192.168.0.8）和MAC地址绑定吗？

ISA Server直接使用自己ARP缓存中的静态绑定项来发送数据，而不是使用收到的Ping请求数据包中的源MAC地址来作为目的地址。

因此，Fake认为此数据包不是发给自己的，不会处理此数据包，所以认为没有Ping回复数据包，自然就是超时了。

最后说一下，

我不推荐大家使用静态IP地址和MAC地址的绑定，这会带来更多的管理负荷。你可以利用ISA Server强大的身份验证功能，结合IP地址来进行管理，这样具有更好的效果。也请不要在论坛问我ARP命令是如何使用的，Windows的帮助是最好的老师。

#### Tripwire {#tripwire}

对unix管理员来说，主机系统的安全一直是个课题，一方面管理员通过更新patch，安装软硬件防火墙等手段努力使自己的系统可靠性增强，而另一方面 unix操作系统的漏洞总是不断被发现并被公布出来，如BUGTRAQ这样的安全列表，从这个角度上可以很绝对的说，互联网上没有安全的主机。任何一台放在Internet上的主机被入侵的潜在可能性是不可逃脱的，而且，对入侵者而言，利用漏洞进入系统往往只是第一步，如果想得到更多的，如超级用户的密码，数据库的口令等，往往需要下点功夫，最便捷也是最有效的就是改动或特洛伊化受侵害的主机上的文件，如放置自己的监听程序，替代某些关键文件，修改编辑可信文件，设置suid文件等。

　　一些管理员通unix自带的命令来检查文件的安全性，如检查文件生成的时间戳，但这样的可靠性微乎其微，有经验的入侵者可以很轻松的修改文件生成时间，有兴趣的管理员可以试试以下操作：

　　# echo &quot;+ +&quot; &gt; /.rhosts

　　这一步生成一个.rhosts文件，看看它的时间。

　　# ls -l /.rhosts

　　-rw-r--r-- 1 root other 4 Jul 2 16：45 /.rhosts

　　好，我们如下操作看看会怎么样?

　　# touch -r /bin/sh /.rhosts

　　#ls -l /.rhosts

　　-rw-r--r-- 1 root other 4 Apr 5 16：32 /.rhosts

　　我们看到时间戳已经变了。变成了一个&quot;老&quot;文件，这样很可能就会逃脱管理员的视线。比如，入侵者替换掉了su文件，在正当用户每次试图su时，这个特洛伊化的su文件都会读取口令并将口令记载下来，然后才把控制权交给真正的su程序，口令通过这种途径泄密了，虽然这不是管理员所期望的，但毕竟unix太大太复杂，发现起来很困难。

　　Tripwire就是解决这一问题的经典工具，它是目前最为著名的unix下文件系统完整性检查的软件工具，这一软件采用的技术核心就是对每个要监控的文件产生一个数字签名，保留下来。当文件现在的数字签名与保留的数字签名不一致时，那么现在这个文件必定被改动过了