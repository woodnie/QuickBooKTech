### POSIX {#posix}

POSIX

Unix 1969 年诞生于 AT&amp;T 贝尔实验室，并在 1973 年使用 C 语言进行了重写，从此就具有了很好的可移植性。但是当 AT&amp;T 在 1984 年由于分拆而得以进入计算机领域的市场之后，却引发了 Unix 业界的一场大战。当时最为主要的两个版本是 AT&amp;T 的 System V 和伯克利的 BSD。二者在技术方面（例如终端）和文化方面都存在很多分歧，导致应用程序很难在不同的系统上平滑地进行移植，为了解决这个问题，IEEE（Institute of Electrical and Electronic Engineers）的 1003 委员会着手开发了一系列标准，这就是后来的 POSIX（Portable Operating System Interface for UNIX）标准。其目的是为那些兼容各种 UNIX 变种的应用程序制定应用程序编程接口（API）规范，从而确保这些应用程序的兼容性。这些标准后来被 ISO/IEC 采纳，成为 ISO/IEC 9945 标准。

POSIX 在 15 份不同的文档中对操作系统与用户软件的接口进行了规范，主要内容包括3个部分：

POSIX 系统调用

POSIX 命令和工具

POSIX 兼容测试

同时还提供了一套 POSIX 兼容性测试工具，称为 PCTS（POSIX Conformance Test Suite）。

后来 POSIX 标准又进行了很多扩充，主要包括：

POSIX.1，核心服务：主要集成了 ANSI C 标准，包括进程创建和控制、信号、浮点异常、段错误、非法指令、总线错误、定时器、文件和目录操作、管道、C 标准库、I/O 端口和控制

POSIX.1b，实时扩展：包括优先级调度、实时信号、时钟和定时器、信号量、消息传递、共享内存、异步和同步 I/O、内存锁

POSIX.1c，线程扩展：包括线程创建和控制、线程调度、线程同步、信号处理

POSIX 最初的设计目标是为 Unix System V 和 BSD Unix 等 Unix 系统上的特性制定规范，使其可以实现更好的可移植性。但是很多其他系统都也兼容POSIX 标准。例如，微软的 Windows NT 就兼容 POSIX 标准的实时部分（POSIX.1b），而 RTOS（LynxOS real-time operating system）也与 POSIX 标准兼容。Windows 上可以通过安装 Windows 的 Services for UNIX 或 Cygwin 来增强对 POSIX 标准的兼容度。

Open Group

Open Group 是现在 Unix 商标的拥有者，其前身是 X/Open。X/Open 是 Unix 厂商在 1984 年成立的一个联盟，它试图为众多 Unix 变种定义一个安全公共子集，因此即使在 Unix 混战的年代，也得到了比较好的发展。在 1993 年，包括主要 Unix 公司在内的75 家系统和软件供应商委托 X/Open 为 Unix 制定一个统一的规范。X/Open在现有标准基础上，增加了对终端进行处理的 API 和 X11 API，并全面兼容 1989 ANSI C 标准，最终诞生了第一版本的单一 Unix规范（Single Unix Specification，简称 SUS）。

X/Open在 1996 年与 OSF（开放软件基金会）进行合并，成立了 Open Group 组织，专门从事开放标准的制定和推广工作，并对很多领域提供了认证，包括 Unix 操作系统、Motif 和 CDE（Common Desktop Environment）用户界面。

Austin Group

Austin Group 是在 1998 年成立的一个合作技术工作组，其使命是开发并维护 POSIX.1 和 SUS 规范。Austin Group 开发规范的方法是&quot;write once, adopt everywhere&quot;，即由 Austin Group 制定的规范既会成为 IEEE POSIX 规范，又会成为 Open Group 的 技术标准规范，以后又会被采纳为 ISO/IEC 的标准。新开发的规范后来就被标准化为 ISO/IEC 9945 和IEEE Std 1003.1，并成为 SUSV3 的核心部分。

这种独特的开发模式最大限度地利用了业界领先的工作成果，将正式的标准化工作转化成了一个唯一的行为，并且吸引了广泛的参与者。Austin Group 目前有 500 多个参与者，工作组的主席是 Open Group 的 Andrew Josey。