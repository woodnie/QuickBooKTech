### LSB {#lsb}

LSB

在90 年代中期，Linux 也开始了自己的标准化努力。实际上，Linux 一直都试图遵守 POSIX 标准，因此在源代码级上具有很好的兼容性，然而对于 Linux 来说，仅仅保证源码级的兼容性还不能完全满足要求：在 Unix 时代，大部分系统都使用的是专有的硬件，软件开发商必须负责将自己的应用程序从一个平台移植到其他平台上；每个系统的生命周期也很长，软件开发商可以投入足够的资源为各个平台发布二进制文件。然而 Linux 使用的最广泛的 x86 通用平台，其发行版是如此众多，而发展却如此之快，软件开发商不可能为每个发行版都发布一个二进制文件，因此就为 Linux 上的标准化提出了一个新的要求：二进制兼容性，即二进制程序不需要重新编译，就可以在其他发行版上运行。

实际上，在 Linux 社区中第一个标准化努力是文件系统层次标准（Filesystem Hierarchy Standard，FHS），用来规范系统文件、工具和程序的存放位置和系统中的目录层次结构，例如 ifconfig 命令应该放在 /usr/bin 还是 /usr/sbin 目录中，光驱应该挂载到 /mnt/cdrom 中还是 /media/cdrom 中。这些需求最终共同促进了 Linux Standard Base（LSB）项目的诞生。

LSB目前是 FSG（Free Standards Group）中最为活跃的一个工作组，其使命是开发一系列标准来增强 Linux 发行版的兼容性，使各种软件可以很好地在兼容 LSB 标准的系统上运行，从而可以帮助软件供应商更好地在 Linux 系统上开发产品，或将已有的产品移植到 Linux 系统上。

LSB 以 POSIX 和 SUS 标准为基础，并对其他领域（例如图形）中源代码的一些标准进行了扩充，还增加了对二进制可执行文件格式规范的定义，从而试图确保 Linux 上应用程序源码和二进制文件的兼容性。

LSB简介

LSB 是 Linux 标准化领域中事实上的标准，它的图标（请参看图 1）非常形象地阐述了自己的使命：对代表自由的企鹅（Linux）制定标准。给定企鹅的体形和三维标准之后，软件开发者就可以设计并裁减出各色花样的衣服（应用程序），这样不管穿在哪只企鹅身上，都会非常合身。

图1\. LSB图标

在现有标准基础上，LSB 制定了应用程序与运行环境之间的二进制接口，这主要是基于以下标准：

Single UNIX Specification（SUS）

System V Interface Definition（SVID）

compilers for the Intel Itanium processor

C++ ABI

System V Application Binary Interface（ABI）

同时，LSB 充分吸取了 UNIX 标准化努力所取得经验和教训，回避了这些标准的一些问题。例如，POSIX 仅仅定义了编程接口的标准，但是它却无法保证二进制的兼容性。而诸如 OSF/1 之类的标准虽然试图解决二进制兼容性的问题，但是限制却太为严格。LSB 在二者之间达成了一个平衡，它包含了一个二进制兼容层，同时消除了 POSIX 与 OSF/1 之间存在分歧的地方。

LSB 对各个库提供的接口以及与每个接口相关的数据结构和常量进行了定义，图2给出了 LSB 3.1 环境中所包含的组件。这些组件包括开发者所需要的共享库（包括 C++），文件系统层次结构（FHS）、对象文件格式、命令和工具、应用程序包、用户和组、系统初始化等所采用的规范：

图2\. LSB 规范包含的组件

组织架构

为了保证 LSB 项目的良好运行，LSB 采用了自己的完整组织架构来负责整个项目的运行，包括主席、选举委员会、执行委员会：

主席：由选举委员会选举产生，任期两年，负责 LSB 项目的整体运作，并对 FSG 和社区代表 LSB项目。目前的主席是 Debian 的创始人 Ian Murdock.。

选举委员会：由所有对 LSB 作出贡献的人组成，负责在主席任期期满时选举下一任主席。

执行委员会：由主席和各个子项目的领导人以及对 LSB

项目有重大贡献的人组成，可以对外作为 LSB 项目的发言人。

工作组

LSB 项目包含几个子项目（也称为工作组），分别负责不同的职责范围，简介如下：

Specification SubGroup：负责开 LSB 规范的开发与维护，还要负责 ISO/IEC 23360（即 ISO LSB 标准的维护）。具体职责如下：

维护 LSB 规范数据库

编写 LSB 规范

开发并维护生成规范文档所需要的工具

LSB Tools SubGroup：负责以下子项目的开发和实现：

SI（Sample Implementation）：遵守 LSB 规范的一个参考实现

Development Environment：开发符合 LSB 规范的应用程序的开发环境

Application Battery：符合 LSB 规范的样例应用程序，例如 lsb-apache

LSB Test SubGroup：负责按照 LSB 规范的定义，开发一些测试套件，来验证用户环境和应用程序是否符合 LSB 规范，主要包括：

LSB Runtime Tests：包括ANSI、POSIX、LSB-OS、线程、用户和组、FHS、国际化、PAM（可插入认证模块）等测试套件

LSB VSW4/XTS5 Test：Xlib11及其扩展库的测试套件

LSB C++ Test：C++ 测试套件

LSB Desktop SubGroup：负责开发与桌面有关的规范的测试套件，用来验证用户环境和应用程序是否符合 LSB 规范，主要包括：

GTK 库

OpenGL 库

PNG12库

JPEG 库

Fontconfig 库

GTK+ Stack 库

QT3/4 库

XML2 库

LSB Future SubGroup：负载开拓 LSB 的新领域，将已经发展比较成熟可以进行标准化但 LSB 尚未涉及的领域纳入 LSB 标准范围内

LSB 的标准化流程

LSB 对于标准的制定和推广遵循务实的原则，它自己不会自行制定标准然后强行要求业界接受，而是把业界中已经成熟的技术和规范采用标准化的形式固定下来，然后大力加以推广，这样可以更广泛地为软件供应商和用户接受。

一个新领域要想纳入 LSB 标准的范畴，必须经过以下 3 个步骤：

1\. 鉴定：确认这个领域是否已经足够成熟，是否具有稳定的 ABI/API，是否需要进行标准化，以及是否依赖于尚未标准化的领域。

2\. 调研：调查上游软件维护者是否还在积极维护，软件是否稳定，是否具有很好的向后兼容性。

3\. 实现：将该领域加入 LSB 数据库、编写规范、编写测试套件、并将其加入开发环境、SI 和 APPBAT。

经过这 3 个步骤之后，LSB Future SubGroup 就会将其提交给 LSB 工作组，将其包含到 LSB 的下一个版本中进行发布，并对外提供认证服务。

认证

在制定好标准并开发出测试套件之后，为了区分系统或应用程序是否兼容 LSB 标准， FSG 提供了 LSB 标准认证服务。任何 Linux 发行版厂商和应用程序开发商都可以进行 Linux 认证，目前提供的认证有两种：

LSB 运行环境：为平台供应商提供的 LSB 标准认证

LSB 应用程序：为应用程序开发商提供的 LSB 标准认证

对于平台供应商来说，经过 LSB 认证之后，就可以确保自己的系统所提供的服务都是标准的，任何遵守 LSB 标准的应用程序都可以很好地在自己的系统上运行；而对于应用程序开发商来说，其意义则刚好相反：不需要担心自己的应用程序在遵守 LSB 标准的系统上的可移植性问题。

LSB 认证过程包含以下步骤：

注册：要进行 LSB 认证的第一个步骤是在 [https://www.freestandards.org/index.php?title=Special:Userlogin](https://www.freestandards.org/index.php?title=Special:Userlogin) 上先创建一个帐号，并注册您的公司和产品。

测试和验证：使用 LSB 提供的测试工具，在您的测试系统上运行，并对结果进行分析（详细内容请参看本系列的下一篇文章），确保您的系统或应用程序遵守 LSB 规范。

最终审计：在准备好正式提交测试结果之后，需要先签署 LSB 认证协议和 LSB 商标许可协议，并向 FSG 支付认证所需要的费用。然后 FSG 会有专人对测试结果进行审计，如果一切正常，就通过了 LSB 认证。通过 LSB 认证的产品都会在 [http://www.freestandards.org/en/Products](http://www.freestandards.org/en/Products) 公开发布。目前已经 Redhat、Suse、RedFlag 等公司都已经通过了 LSB 3.0 的认证，对于 LSB 3.1 的认证正在进展中。

通过 LSB 认证之后，所认证的产品可以贴上 &quot;LSB Certified&quot; 的标签进行销售了。

认证问题报告

在运行 LSB 所提供的测试工具时可能会出现部分测试用例失败的情况，其原因可能是产品本身的问题，例如 FHS 标准要求系统中必须存在 /media/ 目录，而在某些系统中，这个目录可能并不存在，此时就可能会导致相应的测试套件失败，错误信息如下：

10|715 /tset/LSB.fhs/root/media/media-tc 00:55:04|TC Start, scenario ref 720-0

15|715 3.7 5|TCM Start

400|715 1 1 00:55:04|IC Start

200|715 1 00:55:04|TP Start

520|715 1 30056 1 1|Reference 3.11-1(A)

520|715 1 30056 1 2|The /media directory exists and is searchable

520|715 1 30056 1 3|/media: directory not found

520|715 1 30056 1 4|exit code 1 returned, expected 0

220|715 1 1 00:55:04|FAIL

但是有时可能并非是测试环境的问题，而是测试套件本身的问题，或者是由于系统中存在一个公认但却暂时无法修复的问题，此时并不影响 LSB 的认证的结果。如果出现这种问题，测试人员可以将这个问题反馈给 LSB（ [http://www.freestandards.org/cert/prsubmit.php](http://www.freestandards.org/cert/prsubmit.php) ），经过确认之后，LSB 会在一个 waiver 文件中列出这种情况，并将对应的测试套件暂时剔除，并尝试在下一个版本中进行修复。我们也可以从 [http://www.freestandards.org/cert/pr.php](http://www.freestandards.org/cert/pr.php) 上查看已经发现的问题。

LSB 的历史、现状和将来

LSB 项目最初发起于 1998 年 5 月，其项目启动宣言得到了 Linus Torvalds、Bruce Perens、Eric Raymond 等人的签名支持，当时的目标是建立一系列构建 Linux 发行版所采用的源代码应该遵循的标准，并提供一个参考平台。2000 年 5 月，LSB 成为 Free Standards Group（FSG） 的一个工作组。FSG 是一个独立的非盈利组织，专注于通过开发和促进标准来加速开源软件的发展。

从 2001 年 6 月发布第一个正式版本的规范以后，LSB 规范几乎每 6 个月都会进行一次更新。截止到 2005 年 7 月发布的 3.0 版本为止，LSB 重点关注的是服务器端的使用，这与 Linux 在服务器端得到了广泛的应用是一致的。这个规范已经被 ISO 采纳为国际标准 23360。

目前最新的版本规范是 2005 年 10 月发布的 LSB 3.1，目前它可以支持 7 种体系结构：

IA32

IA64

X86_64

PPC32

PPC64

S390

S390x

由于平台的差异，所有的规范除了有一个通用的版本之外，还都存在一个适用于特定平台的版本，其中的内容是完全适用于这个平台的。

与上一个版本相比，LSB 3.1 版本的规范主要是增强了对桌面系统的标准化支持，增加了对 GTK 和 QT GUI 工具包的标准化。另外，LSB 还调整了自己的路线图，以便可以与主流的 Linux 发行商（Redhat、Novell、Asianux、Debian 等）的发行计划更好地吻合，并吸引了更多 Linux 发行商的参与，对开发工具和文档进行了改进，还与各个国家的组织（例如中国电子技术标准化研究所，CESI）进行认证方面的合作。

下一个版本 LSB 3.2 将在 2007 年第二季度发布，将主要增加 freedesktop.org 的标准和跨桌面的交互操作性。

LSB 4.0 将在 2008 年发布，它将实现更好的二进制兼容性，并增加对 Perl、Python、LAMP、Java 等语言的标准化支持。