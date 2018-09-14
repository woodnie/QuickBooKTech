## ability {#ability}

开源监控系统：cacti，ganglia,nagios,MRTG(snmp),Cacti流量,Zabbix分布式

监控工具如Wily Introscope, HP Sitescope, Topaz, Foglight,solarwinds、ipmonitor

熟悉常见扫描工具的使用如Nessus、TcpDump， WireShark，NetCat

扫描工具-Nmap

抓包工具-sniffer和wireshark，tcpdump

熟悉主流IDS、IPS等检测和分析软件

用普通的linux命令查看服务器(top/iostat/vmstat/sar)

熟悉至少一种脚本语言(Shell,Perl,Python)

熟悉Linux系统的优化，比如内核裁减、性能参数调整、安全优化等；

Linux系统的优化，比如内核裁减、系统性能参数调整、安全优化等；

能独立完成Linux服务器的安装、维护和集成, 及软件的安装、故障运维、性能调优, 对于服务器的排错有一定经验；

了解Linux内核，具有编译定制Linux内核的经验优先

安装配置unison,memcache服务

精通weblogic，熟悉websphere,tuxedo,jboss等中间件产品。

熟练掌握Weblogic中间件部署配置，运行和日志分析。

具有能使用wlst方式管理维护weblogic能力，熟悉性能调优。

熟练掌握JVM的内部工作原理，能使用相关的工具进行分析定位问题。

网络文件系统：ASM, OCFS, RAW

版本控制：cvs svn

www.zebra.org

www.quagga.net

OpenVZ+Vtonf

详细出处参考： [http://www.jb51.net/article/23278.htm](http://www.jb51.net/article/23278.htm)

vps

RHCA

linux C

linux 嵌入式 ARM Qt

linux java

CCNA

ORACLE

Android

EXPECT工具

CommVault、NBU、BE、Bakbone 备份工具

EN:

performance  系能

optimizing 优化

deploy 部署

Analysis   分析

maintenance 维护

middleware 中间件

storage 存储

virtualization 虚拟化

HPC集群，HA集群，以及LB集群

MySQL

关系型数据库存储系统，我们的DBA团队很强大，每人管理上百台MySQL服务器，其他就不多说了，网上资料太多了

Tokyo Cabinet

一个key-value的存储引擎，日本人开发，国内很多公司也开始使用，我们内部很多地方也用它来代替MySQL来做存储，比如我们的搜索结果页的用户资料，就是用它来做一层MySQL外的冗余存储，目的是加快搜索结果页的显示。在key-value并需要持久存储的场景下，用它比MySQL更有效，Cabinet本身只是一个存储引擎，没有网络处理能力，你可以用它作为自己的某个系统的下层存储引擎，更好的是搭配Tokyo Tyrant使用。

Tokyo Tyrant

一个支持Memcached传输协议的网络接口，由Tokyo Cabinet的作者开发，目的是为Tokyo Cabinet提供网络接入能力，即Tokyo Tyrant处理网络连接，协议解析，然后调用Tokyo Cabinet的API来完成持久化存储。

ICE

一个跨语言的网络通讯框架，框架本身提供了强大的通讯能力，管理工具，负载均衡方案，其跨语言能力也是一个很大的亮点，基于这个框架之上，我们选用合适的语言来提供合适的服务，比如我们使用C++来开发Cache服务，使用Java来开发一些逻辑服务。框架本身可以很重，也可以很轻，具体要看你怎么用：）

Memcached

一个纯内存的key-value的cache系统，高效、稳定，使用广泛，如果你连它都没听说过就太out啦，memcached本身不具备分布式能力，需要依靠Client来实现分布，这里强调一点的是，你应该选择一致性Hash来做key的分布。各种语言的client都有，我们使用spymemcached作为java的Client，spymemcached是一个异步的NIO的memcached client，对网络IO的处理非常的精巧，也更加高效，同时因为提供异步操作方式，可以让你对Memcached的操作有更好的控制能力，Memcached到1.4.0版本之后，开始支持binary protocol，spymemcached对其也支持的比较好，使用binary protocol可以提高对协议的解析效率和网络IO的读写效率。

上面说到我们使用ICE自己开发了Cache服务，为什么我们还要用Memcached呢？主要在对Cache的操作粒度不一样，Memcached对Cache对象以binary byte作为一个整体来操作，需要频繁的序列化和反序列化，我们使用ICE提供的Cache服务，可以以Cache对象的一个或者多个字段来操作，比如一个用户对象，我们可以只更新它的姓名，而Memcached

Nginx

高效、稳定的Web Server，我们利用其代理能力，做跨IDC的请求代理，同时也将其和我们的Resin(Java Web 容器)搭配，放在Resin的前面来解决Resin的对网络连接处理能力弱的问题，在一些小地方也用它来做7层的负载均衡

Resin

一个Java Web Server，比Tomcat更高效，是我们主要的Java Web容器

Squid

代理服务器，我们用他来做图片文件的反向代理缓存

LVS

能提供4层的负载均衡，高效、高可用，高并发。我们用他替代了很多硬件的负载均衡设备

Struts

Java web框架，不过这个已经是历史了，我们开发了一套自己的Web框架替代了它，未来我们也会把我们的内部的这套Web框架开源出来

Lucence

基于Java的搜索引擎框架，用它我们构建了一个搜索集群来提供搜人的服务

Netty

一个Java的网络框架，和apache的mina类似，但比mina更高效，我们用来做一些小的服务

Ganglia

一个监控系统，帮组我们了解我们每台Server的资源利用情况

JWhoisServer 是一个小型快速高可配置的 RFC 3912 兼容的 whois 服务器软件，采用 Java 语言编写，使用数据库作为存储引擎，从 0.3.0 版本开始支持 INET lookup。

phpWhois -base class to do whois queries with php