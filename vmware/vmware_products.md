## VMware products {#vmware-products}

VMware Workstation

VMware 工作站（VMware Workstation）是VMware公司销售的商业软件产品之一。该工作站软件包含一个用于英特尔x86相容容电脑的虚拟机套装，其允许用户同时创建和运行多个x86虚拟机。每个虚拟机实例可以运行其自己的客户机操作系统，如（但不限于）Windows、Linux、BSD变生版本。用简单术语来描述就是，VMware工作站允许一台真实的计算机同时运行数个操作系统。其它VMware产品帮助在多个宿主计算机之间管理或移植VMware虚拟机。

由于企业市场中高速增加的服务器的巨大数量，VMware工作站的声望获得了增长[来源请求]。将工作站和服务器转移到虚拟机环境可使系统管理简单化、缩减实际的底板面积、并减少对硬件的需求。

主要限制（至2010年10月）：

3D 加速功能不支持 Windows XP 客户机。

VMware Player

用于为虚拟机提供宿主服务的免费软件产品VMware Player可运行由其它VMware产品产生的客户虚拟机，同时也可以自行创建新的虚拟机。

VMware的官方网站提供了多个经过预先配置的操作系统和应用程序的免费虚拟盘映像，这之中有不少是社会募捐的[1]。也存在着可用来创建虚拟机，以及对VMware虚拟硬盘和软盘映像文件进行挂装、操作及转换的免费工具，因此VMware Player程序的用户实际上可以无须付费而创建、运行和维护虚拟机（即使是用于商业目的）。

VMware Server

在2006年2月6日VMware发布了VMware Server产品的1.0版本，取代原先的VMware GSX Server[2]。VMware服务器可以创建、编辑、运行虚拟机。除了具有可以运行由其它VMware产品创建的虚拟机的功能外，它还可运行由微软Virtual PC产品创建的虚拟机。VMware国际公司将VMware服务器产品作为可免费获得的产品，这是因为希望用户们最终能选择升级至VMware ESX服务器产品。

VMware国际公司不正式支持运行于Windows XP或专业版Windows 2000上的VMware服务器产品，这不同于VMware工作站产品。然而，已有用户报告了在专业版Windows XP下成功安装并提供VMware服务器功能的例子（但有个别限制要求）[3]。VMware国际公司提供了一个受支持的宿主操作系统的清单[4]。

VMware ESX服务器

ESX 服务器使用了衍生自斯坦福大学（Stanford Univ.）开发的SimOS核心，该核心在硬件初始化后替换原开机的Linux内核。ESX服务器2.x的服务控制平台（亦称为&quot;COS&quot;或&quot;vmnix&quot;）是基于Red Hat Linux 7.2的。ESX服务器3.0的服务控制平台源自一个 RedHat 7.2的经过修改的版本--它是作为一个用来加载vmkernel的引导加载程序运行的，并提供了各种管理界面（如CLI、浏览器界面MUI、远程控制台）。该虚拟化系统管理的方式提供了更少的管理开销以及更好的控制和为虚拟机分配资源时能达到的粒度（指精细的程度）；这也增加了安全性，从而使VMware ESX成为一种企业级产品。

VMware ESXi 服务器

Vmware ESXi Server是删减部份ESX Server功能之后提供的免费版本，。

VMware vSphere

VMware vSphere，原称为VMware Infrastructure，是一整套虚拟化应用产品，它包含VMware ESX Server 4、VMware Virtual Center 4.0、最高支持8路的虚拟对称多处理器（Virtual SMP）和VMotion，以及例如VMware HA、VMware DRS和VMware统一备份服务等分布式服务。 VMware国际公司在2009年4月发布了VMware vSphere 4。该套装提供六个档次的组合方案

数据中心

VMware国际公司对数据中心应用提供两种主要产品：VMware ESX和VMware服务器（旧称为VMware GSX）.

VMware ESX服务器是作为VMware用于在数据中心应用中运行企业级应用的旗舰产品。由于ESX是在&amp;apos;近硬件&amp;apos;层级上加载的，它能使x86的利用效率提高60%到80%。

数据中心亦可使用VMware服务器产品运行，但运行该产品须依赖于宿主环境的基本操作系统；此外，在运行软件的额外层面时也会产生对机器的附加开销。然而VMware服务器产品具有一点超过ESX产品的优势：它支持的设备的规格更多，例如可支持USB连接方式和某些PCI设备。

亦请注意VMware ACE产品。

其它产品

其它三种与ESX协同运行的产品是：虚拟中心（VirtualCenter）、VMotion和P2V（将物理计算机运行环境直接移植为虚拟机的工具）。

虚拟中心可用来监视和管理多个ESX或GSX服务器。

VMotion可用来在服务器之间实现几乎无停滞地移动运行中的虚拟机。

P2V允许用户通过使用映像软件，将一台物理的服务器制作为虚拟机映像，从而创造出一个从物理机到虚拟机的重现。它用虚拟的驱动文件代替了实际的驱动文件，并且在VMware的数据存储中创建出机器空间。