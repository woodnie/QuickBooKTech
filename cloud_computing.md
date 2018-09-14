# Cloud Computing {#cloud-computing}

OpenStack 、桉树、vCloud Director对比

[http://cloud.csdn.net/a/20120723/2807611-Cloud-platform-comparison.html](http://cloud.csdn.net/a/20120723/2807611-Cloud-platform-comparison.html)

云服务模式：

?SaaS（软件即服务）

?PaaS（平台即服务）

?IaaS（基础架构即服务）

**SaaS篇**

消费者不用操心与服务有关的任何问题或麻烦。服务提供商对应用程序享有非常高的管理控制权，负责更新、部署、维护和安全。提供商对应用程序行使最终管辖权。比如说，Gmail就是一种SaaS，谷歌是提供商，我们大众则是消费者。我们对Gmail享有的管理权和用户级控制权非常有限，不过消费者可以通过设置来采取一系列有限的操作，比如启用优先收件箱、签名和撤销发送邮件等。

SaaS用户是哪些？

除了组织和企业外，SaaS用户/订户还可以是你我这样的个人。在大多数情况下，使用费按用户数量来计算。比如说，Google Apps最多可供10个电子邮件帐户免费使用；但是如果用户数量超过10个，Google Apps for Business每月每个用户收费5美元。

何时/为何应该选择SaaS？

如果你想要致力于业务，而不是把时间浪费在更换坏掉的故障、管理IT基础架构；最重要的是，不想把时间浪费在聘请和留住IT人员上。

你应该选用哪种SaaS？

?使用SaaS最有效的是云端生产力和协作应用程序（如Google Apps），以及在线项目管理应用程序（如DeskAway以及Zoho Mail/Chat/Docs/Project/Sheet/Writer等）。

?客户关系管理（CRM）应用程序--Impel CRM、Salesforce.com和微软Dynamics。

?基于云的存储和共享服务，如Dropbox、Skydrive（Windows Live）、亚马逊简单存储服务（S3）、Google Docs、Box.net和Mozy。

?中小企业/中小公司可以选用EazeWork（用于人力资源、工资处理和销售）

**PaaS篇**

简单地说，PaaS是可以在上面开发、测试和部署软件的一种平台；这意味着，软件的整个生命周期都可以在PaaS上完成。这种服务模式专门面向应用程序的开发人员、测试人员、部署人员和管理员。这项服务提供了开发云SaaS应用程序所需要的一切资源。

PaaS通常包括了开发环境、编程语言、编译程序、测试工具和部署机制。在一些情况下，比如谷歌应用引擎（GAE），开发人员可以下载开发环境，然后在开发人员自己的基础架构中本地使用开发环境；或者开发人员可以通过浏览器，使用提供商的基础架构中的工具。

PaaS用户是哪些？

独立软件开发商（ISV）、IT服务提供商或者甚至想开发SaaS的开发人员个体。

何时/为何应该选择PaaS？

你完全致力于开发应用程序，其他一切都将由平台来处理。

你应该选择哪种PaaS？

?GAE在Java和Python开发人员个体当中比较受欢迎。

?微软Windows Azure针对企业级用户群。ASP.Net（C#、VB.Net）开发人员会发现采用Windows Azure很容易。

?亚马逊也向前迈出了一步，提供PaaS：Beanstalk（这让Java开发人员多了一个选择）。

?几家总部设在印度的PaaS提供商（如OrangeScape和Wolf Frameworks）正凭借其5G可视化PaaS，在市场上掀起了动静。OrangeScape应用程序可以在所有主要的云平台上运行，包括谷歌应用引擎、微软Azure、IBM SmartCloud、亚马逊弹性计算云（EC2）或数据中心，没必要改写应用程序。

?Engine Yard和Heroku是面向Ruby on Rails（RoR）的领先的云PaaS。Heroku（已被Saleforce.com收购）也是用于开发Facebook应用程序的优先PaaS。

?PHP开发人员可以在PHP Fog和CloudControl之间进行选择。

?想选择支持多语言的应用平台，不妨考虑DotCloud。

?总部设在印度的Ozonetel Systems提供KooKoo PaaS，提供云电话服务。

**IaaS篇**

你需要虚拟计算机、云存储、防火墙和配置服务等网络基础架构部件吗？IaaS正是你应该选择的云服务模式。系统管理员是这种服务的一类用户。使用费可以按多个标准来计算，比如每个处理器小时、每小时存储的数据（GB）、所用的网络带宽、每小时所用的网络基础架构以及所用的增值服务（如监控和自动扩展等），不一而足。

IaaS用户是哪些？

你知道《开心农场》和《黑帮战争》吗？是的，它们是由Zynga.com开发的最受欢迎的两款Facebook游戏。每个月超过2.3亿个用户在亚马逊AWS上运行12000多台服务器。每当游戏开发商推出一款新游戏，开始是使用几台服务器，然后实时扩增服务器容量。

为了防止服务器遭到分布式拒绝服务攻击（DDOS），颇有争议的维基解密网站（Wikileaks）曾托管在亚马逊AWS上。现在，这个网站似乎搬回到了瑞典的主机上。

其中最重要的用户是SaaS和PaaS提供商，它们与IaaS提供商托管在一起。总部设在印度的在线订票服务商redBus。

何时/为何应该选择IaaS？

IaaS对于不知道新推出的应用程序/网站会有多成功的创业公司来说非常有用。你可以选择多个操作系统、平台、数据库和内容分发网络（CDN）--它们都在一个地方。

注意：由于经济原因，目前不建议把每月访客量不到10000人次的静态网站托管在IaaS平台上。如果你使用亚马逊AWS，可能每月需要付费18美元左右。

你应该选择哪种IaaS？

亚马逊是IaaS领域的先驱。其他领先的提供商包括Rackspace、GoGrid、Joyent、Rightscale和Terremark（已被美国电信运营商韦里逊公司收购）。

想选择总部设在印度的IaaS，不妨考虑下面两家提供商：

?NetMagic Solutions

?InstaCompute（隶属印度电信运营商塔塔通信公司）

### OpenStack {#openstack}

[http://www.openstack.org/](http://www.openstack.org/)

[http://os.51cto.com/art/201111/304714.htm](http://os.51cto.com/art/201111/304714.htm)

[http://www.vpsee.com/2011/05/install-openstack-nova-on-ubuntu/](http://www.vpsee.com/2011/05/install-openstack-nova-on-ubuntu/)

### Eucalyptus {#eucalyptus}

### zCloud {#zcloud}

### Amazon Web Services {#amazon-web-services}

pscp -i D:\wood\Sync\AWS-Free-Californai.ppk ubuntu@54.215.243.45:/home/ubuntu/.ssh/authorized_keys D:\wood\Sync

#### Untitled {#untitled}

54.183.208.120

54.183.255.4

### Tools {#tools}

Introduction 概述        

State of the practice in analytics

数据分析的现状与趋势

Big Data Overview

深入认识大数据        The role of the Data Scientist

数据科学家的角色与任务        Big Data Analytics in industry verticals

大数据分析的行业应用

Introduction to Big Data Analytics

大数据分析技术与应用概况

       Key roles for a successful analytics project

数据分析项目成功的关键因素        Main phases of the lifecycle

数据分析过程与周期中的关键节点        Developing core deliverables for stakeholders

完成向涉众交付的开发核心

End-to-end data analytics lifecycle

端到端的数据分析过程与周期

       Introduction to R

R语言介绍        Analyzing and exploring data with R

使用R语言进行数据分析        Statistics for model building and evaluation

数据统计模型构建和评估

Using R to execute basic analytics methods

使用R语言进行基础的数据分析

Adv. Methods  高级方法        K-Means Clustering

K-Means算法        Association Rules

关联规则        Linear and Logistic Regression

线性回归和逻辑回归        Naive Bayesian Classifier

朴素贝叶斯分类器        Decision Trees

决策树        Time Series Analysis

时序分析        Text Analysis

文本分析

Advanced analytics and statistical modeling for Big Data - Theory and Methods

大数据分析与统计建模 - 理论与方法

Tools 工具        

Using MapReduce/Hadoop for analyzing unstructured data

使用MapReduce/Hadoop分析非结构化数据

Hadoop ecosystem of tools

围绕Hadoop的工具        In-database Analytics

数据库内分析        Big Data Analytics in industry verticals

大数据分析的行业应用

Advanced analytics and statistical modeling - Technology and Tools

大数据高级分析与统计建模 - 技术与工具

Lab 实践

Hands-on Application of Analytics Lifecycle to a Big Data Analytics Problem

基于分析过程与周期应对大数据挑战

How to operationalize an analytics project

如何实施分析项目        Data Visualization Techniques

数据可视化技术        Creating the Final Deliverables

创建可交付的最终成果

Endgame, or Putting it all together

将技术、方法及工具应用于实践

### 2015Guide to the Open Cloud {#2015guide-to-the-open-cloud}

Linux 基金会已公布了第二届年度开源云指南

下面是2015年的开放云指南中，按类别区分的17个新项目。

虚拟机管理程序和集装箱（Hypervisor and container）

   LXC：Linux 内核，其中的 cgroup，命名空间和安全模块中按功能启用轻量级虚拟机。用户空间工具坐标内核的特性和操纵容器的图像来创建和管理系统或应用程序的容器。

云操作系统*（Cloud Operating Systems）

   阿帕奇Mesos：一个开源的集群管理工具，也被描述为一个操作系统内核的数据中心。

   CoreOS：一个轻量级的Linux发行版专为运行大型群集部署。应用程序容器内运行，独立于操作系统。

   OSV：OSV是一个开源云操作系统旨在运行在hypervisor之上的单个应用程序。

平台即服务（Platform-as-a-Service）

   Apache Stratos：开源 PaaS 的企业架构，帮助运行 Apache Tomcat，PHP 和 MySQL 的应用程序。

   DEIS：DEIS 是一个开源的 PaaS，建立在 Docker 和 CoreOS 系统上，提供了一个轻量级的 PaaS，仿 Heroku 的风格的工作流程。

配置和管理工具

   Ansible：开源云的自动化软件，用于对多层体系结构的应用程序部署和配置管理。

   Kubernetes：一个为 Docker 容器集群编排和管理工具。

   ManageIQ：混合云管理工具来管理云和虚拟化平台上运行的服务。

存储技术

   Apache Cassandra：一个高度可扩展，最终一致，分布式的，结构化的 key-value 存储。

   CouchDB：分布式文档数据库系统。

   MongoDB：高性能数据库文件。

   Redis：一个开源键值缓存和存储。

   Swift：一个高度可用的，分布式的，最终一致的对象存储。

SDN和NFV项目

   OpenDaylight：网络编程一个开源平台，使 SDN 和 NFV。该软件组件包括一个完全可插入控制器，接口，协议插件和应用程序。

   Open vSwitch：旨在使庞大的网络自动化，同时还支持标准的管理接口，分布式计算的开源虚拟交换机。

   OpenContrail：一个开源软件定义网络项目，提供所有必要的组件，网络虚拟化，包括一个SDN控制器，虚拟路由器，分析引擎的 API。（英文：Linux，译者跳骚图）