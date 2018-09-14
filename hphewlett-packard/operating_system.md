## Operating System {#operating-system}

#### HP Unix {#hp-unix}

[http://www.hp.com/softwarereleases/releases-media2/HPEredesign/pages/hpux.html](http://www.hp.com/softwarereleases/releases-media2/HPEredesign/pages/hpux.html)

HP-UX operating system

release history

End of factory support

HP-UX version        Introduced                End of factory support

11i v3                February, 2007                December 31, 2020 (HP 9000)

                                       December 31, 2022 (HP Integrity)

11i v2                September, 2003        December 31, 2015

11i v1                December, 2000                December 31, 2015

11.0                November, 1997                December 31, 2006

Introduced: Date of product introduction, not necessarily the date of first customer shipments

End of Factory Support: Support no longer available from HP standard factory support, but limited support may be offered to an additional duration.

Please note that the end of factory support in the above chart is subject to change without notice, and will be updated by HP as needed. www.hp.com/go/hpux11iv3

Release name        Operating system release identifier

HP-UX 11.0        B.11.00

HP-UX 11i v1        B.11.11

HP-UX 11i v2        B.11.23

HP-UX 11i v3        B.11.31

Please note: The expected turnaound time for database change requests is ten (10) business days from receipt of a completed form.

HP-UX Certified System Administration

第1篇 UNIX系统基础

HP Unix

第1章 开始使用UNIX

第1章 开始使用UNIX

1.1 UNIX shell

     HP-UNIX 缺省shell:POSIX shell

1.2 HP-UX的登录和注销

1.2.1 超级用户

        root UID=0

1.2.2 登录

1.2.3 shell提示符

        #非root

        $root

1.2.4 注销  

        #exit

        $exit

1.3  主目录

       /root

       /home/...

1.4 使用HP-UN命令

1.4.1 外部命令、内部命令

       外部命令：

       内部命令：内置在shell中的命令

1.4.2 改变口令

        6-8个字符

        至少有两个字母

        至少有一个数字或者特殊字符

1.4.3 历史与回调命令

       Esc+K (一次一个历史命令)

       $history

       $history  数字

1.4.4 命令别名

       $alias dir=ls

1.5 shell启动文件

    登录系统时，自动执行的命令。

1.5.1 系统启动文件

       /etc/profile

       系统启动文件对所有用户有效，一般用于用户的全局配置

1.5.2 用户启动文件

        /root/.profile

        /home/.../.profile

        用户启动文件针对每个用户定制启动文件，一般用于用户特定的配置

1.6 一些简单的HU-UN命令

$ w

# uptime -w

第2章 管理文件和目录

第2章 管理文件和目录

2.1 基本的文件操作

2.1.2 创建文件

        $cat &gt; newfile

       &lt;Enter&gt;   #换行

       &lt;Ctrl +d&gt; #结束

2.1.2 列举文件

       $ ls

       $ ls -l  

       $ ll

       $ ls -f

2.1.3 删除文件

       $ rm newfile

note：rm在正常情况下删除文件没有信息输出提示，最好将alias=rm -i 添加到环境变量中

2.1.4 显示文件命令

       $ cat newfile

2.2 文件命名规则

2.2.1 文件名的一般规则

       1)有效长度256个字符

       2)所有大小写字母

       3)数字

       4)特殊字符

       5)大小写敏感

2.2.2 隐藏文件

以. 开头的文件

$ ls -a

note：rm在删除一个目录中的全部文件时，隐藏文件是不被删除的

2.3  操作目录

2.3.1 创建目录

        $ mkdir newdir

        $ ls f  

        $ ls -f    #短格式区分文件和文件夹

2.3.2 删除目录

        $ rmdir     空目录

        $ rm -r    非空目录

        $ rm -ri   非空目录  # -i 给予交互式的提问

2.3.3 理解目录结构

        .参照当前目录

        ..参照当前目录的父目录

2.3.4 遍历文件系统

        $ cd

        $ pwd

2.4 拷贝和移动文件

2.4.1 拷贝文件

$ cp

2.4.2 移动和重命名

$ mv

$ mv -i    #  -i：给予交互式的提示信息

1)重命名：源文件和目标文件都没有申明任何路径

2)移动：源或者目标文件名任何一个包含路径，即为移动

2.5 通配符

2.5.1 使用*通配符：匹配0个或者多个

        $ ls myfie*

2.5.2 使用？通配符：匹配一个

        $ ls myfile?

2.5.3 使用[ ]通配符

        $ ls myfile[1-10]

        $ ls myfile[0,1,2,3]

2.6 文件类型

file 命令通过查找文件中的幻数，使用 /etc/magic文件来确定文件的不同类型

2.6.1 文本文件

       $ file myfile

       myfile: ASCII text

2.6.2 目录

        $ file mydir

        mydir: directory

2.6.3 可执行文件

         $ file /bin/ls

         /bin/ls: executable

2.6.4 共享库

        file /lib/libwrap.so.0.7.6

        /lib/libwrap.so.0.7.6:shared object

2.6.5 shell脚本

       file /etc/init.d/network

       /etc/init.d/network: Bourne-Again shell script text executable

2.7 搜索文件内容

       $ grep  keywords /dir/file  #查找包含关键字的文件

2.7.1        grep key_words file

       grep -i key_words file

       grep -v key_words file

2.7.2        grep &quot;stream&quot; file

2.7.3        在多个文件在查找一个字符串

       $ grep root /etc/passwd /etc/group

       /etc/passwd:root:KA9xnx6fNb8Dc:0:3::/root:/sbin/sh

       /etc/group:root::0:root

       /etc/group:other::1:root,hpdb

       /etc/group:bin::2:root,bin

       /etc/group:sys::3:root,uucp,precise

       /etc/group:adm::4:root,adm

       /etc/group:daemon::5:root,daemon

       /etc/group:mail::6:root

       /etc/group:lp::7:root,lp

2.8 查找文件

$ fine

2.9 文件处理命令

2.9.1        head / tail

2.9.2        $wc

       $wc -l

2.9.3        $ln

       $ln -s

第3章 环境变量

第3章 环境变量

3.1 环境变量 和 shell变量

环境变量：全局变量，被所有子进程继承，通常包括系统特殊信息

shell变量：局部变量，不被子进程继承，通常用于保存shell程序的临时值

3.2设置和显示变量

$ NAME=&amp;apos;wood&amp;apos;

$ echo $NAME

$ echo NAME

3.2.1.列出所有变量

$ set

$ set | less  

3.2.2 包含多个字的变量

note： &amp;apos; &amp;apos; 和 &quot; &quot;之间有细微的差别

[root@node ~]# NAME=&amp;apos;wood&amp;apos;  

[root@node ~]# NAME=&amp;apos;$NAME nie&amp;apos;    # &amp;apos; &amp;apos; 单引号

[root@node ~]# echo $NAME      

$NAME nie

[root@node ~]# NAME=&amp;apos;wood&amp;apos;      

[root@node ~]# NAME=&quot;$NAME nie&quot;   # &quot; &quot; 双引号

[root@node ~]# echo $NAME      

wood nie

{ } ：引用其他变量

[root@node ~]# NAME=&amp;apos;wood&amp;apos;  

[root@node ~]# HI=&quot;Hello,I am ${NAME} ! &quot;

**3.2.3 修改变量**

1）直接赋值

$ NAME=wood

$ echo $NAME

wood

$ NAME=not_wood

$ echo $NAME

noT_wood

2）修改值

$ NAME=wood

$ echo $NAME

wood

[root@node ~]# NAME=&quot;$NAME nie&quot;   # 注意使用双引号&quot; &quot;，而不是单引号&amp;apos; &amp;apos;

[root@node ~]# echo $NAME      

wood nie

[root@node ~]# echo $HI

Hello,I am wood !

[root@node ~]# HI=&quot;Hello,welcome to `hostname`&quot;       # 反引号``  ：引用其他变量

[root@node ~]# ehco $HI

-bash: ehco: command not found

[root@node ~]# echo $HI  

Hello,welcome to node.domain.org

[root@node ~]# FILES=$(ls /root/)

[root@node ~]# echo $FILES

anaconda-ks.cfg crontab Desktop ifconfig-eth install.log install.log.syslog Mail mbox

3.2.5.删除变量

[root@node ~]# unset NAME

3.3 预定义环境变量

3.4导出变量:

export  导出变量，让当前Shell的子进程也可以使用

e.g.:

[root@node ~]# NAME=&quot;wood&quot;

[root@node ~]# echo $NAME

wood

[root@node ~]# sh

sh-3.2# echo $NAME  

                                             #子shell 无效

sh-3.2# exit

exit

[root@node ~]# export NAME   #导出

[root@node ~]# sh

sh-3.2# echo $NAME               #子shell有效

wood

第4章输入/输出重定向和管道

第5章 使用vi编辑器

第6章正则表达式

6.1 如何执行命令

6.2 定位符

6.2.1        ^

6.2.2        $

6.2.3 删除空白符

       $grep ^$ myfile | wc -l #统计空白行

6.2.4 转义符 \

       $grep \\ #查找&amp;apos;\&amp;apos;

       $grep \^ #查找&amp;apos;^&amp;apos;

       $grep \$ #查找&amp;apos;$&amp;apos;

6.3 元字符

第8章 Unix文件系统

8.3 设备目录

       /dev/rdsk         与物理磁盘有关的基于或裸设备的设备文件

       /dev/dsk         磁盘的块设备文件

8.4/etc/ 目录

8.5 系统二进制目录

       /sbin

       /sbin/init.d

       /sbin/rc.[0-6]

8.7 /stand 内核目录

       /stand/vmunix 内核文件

       /stand/system 配置文件

       /stand/build

8.8 /net 为远程系统加载点预留的名字

8.9 /opt 应用程序目录

8.10 /tmp 临时文件

8.11 /usr 目录

       /usr/bin

       /usr/contrib

       /usr/include

       /usr/lib

       /usr/sbin

       /usr/share/man

8.12

8.12.1

       /var/adm/        系统日志

       /var/adm/cron

       /var/adm/sw        软件安装/删除

       /var/adm/syslog/

       /var/adm/crash

       /var/opt

8.12.2 /var/spool

       /var/spool/lp 打印服务

       /var/mail

       /var/spool

8.12.3        /var/tmp

第9章 POSIX shell

9.1 POSIX shell

                    ____________________________________

                    |  To obtain:          |    Use the command:          |

                    |_______________|____________________        |

                    | POSIX Shell          |  /usr/bin/sh ...              |

                    | Korn Shell          |  /usr/bin/ksh ...            |

                    | C Shell              |  /usr/bin/csh ...            |

                    | Key Shell            |  /usr/bin/keysh              |

                    | Bourne Shell          |  /usr/old/bin/sh ...          |

                    |_______________|____________________|

        文件名补全

9.1.1

9.1.2 资源控制

$ulimit -a

time(seconds)        unlimited

file(blocks)         unlimited

data(kbytes)         393216

stack(kbytes)        8192

memory(kbytes)       unlimited

coredump(blocks)     4194303

nofiles(descriptors) 2048

$man ulimit

1\. ulimit -a

Display all configured values.

2\. ulimit -c

Sets core file size

3\. ulimit -d

Sets data seg size

4\. ulimit -n

Sets Open Files

5\. ulimit -s

Sets stack size

6\. ulimit -u

Sets max user processes

7\. ulimit -t

Sets cpu time

8\. ulimit -v

Sets virtual memory

9\. ulimit -p

Sets pipe size

**9.2 文件名补齐**

       Esc Esc

       Esc -

       Esc +

9.3 历史和命令重输

       $history

       $r _Number_

9.4 命令行编辑

       $Esc K

       VI

9.5 替换

9.5.1 变量替换

       $echo HOME

       $echo $HOME

9.5.2 命令替换

       $echo date

       $echo $(date)

       $echo `date`

9.5.3 波浪号替换

       ~  HOME

       ~+ PWD

       ~- OLDPWD

9.6 设置终端参数

       $stty -a

9.7 作业控制

9.7.1 前台和后台作业

       $ command &amp;        #后台运行command

       $ jobs                #查看后台运行的作业，+ 表示当前作业，- 表示该作业在当前作业之后执行

9.7.2        挂起一个前台作业（把作业放到后台，并停止运行）

       $stty -a |grep susp

       $stty susp ^z #定义使用Ctrl+z来挂起作业

9.7.3 恢复后台作业并把后台作业带到前台

       $jobs                #查看后台作业ID

       $fg %ID        #把后台作业带到前台

9.7.4 把作业移到后台

       $bg %job_ID        #把后台stoped作业Runing起来

9.7.5 停止正在运行的后台作业

9.7.6 等待后台作业完成

       $wait                #等待所有后台作业完成

       $wait job_id        #等待制定ID的后台作业完成

第10章shell编程概述

10.1 shell程序剖析

10.1 shell程序剖析

10.1.1 那个子shell将执行

       #!/usr/bin/shell

10.1.2 shell程序中的注释

       #

**10.1.5 调试shell程序**

       #!/usr/bin/shell -x

10.2 使用变量

10.2 使用变量

       环境变量可以给shell程序传递参数，也可以在shell程序修改环境变量，但程序一旦终止修改就丢失了。

10.3 命令行参数

10.3 命令行参数

10.3.1 使用命令行参数或位置参数

10.3.2 shift

       shift命令用于把命令行参数左移一个位置

       shift 1 #左移一个位置

       shift 2 #左移两个位置

       ...

10.4 交互的shell程序

10.4 交互的shell程序

10.4.1 read命令

       echo &quot;Please input your name: &quot;

       read NAME        

       echo &quot;HEllo $NAME.

10.4.2 echo命令

10.5 退出代码

10.5 退出代码

       echo $?

10.6 test命令

10.6 test命令

       显式模式:test &quot;ABC&quot;=&quot;abc&quot;

       隐式模式:[ &quot;ABC&quot;=&quot;abc&quot; ]

10.6.1 测试数值

10.6.2 测试字符串

10.6.3 测试文件

10.6.4 逻辑操作符测试

10.7 分支

**10.7 分支**

10.7.1 if-then-if

       if expr

       then

               action

       fi

**10.7.2 if-then-else-fi**

       if expr

       then

               action1

       else

               action2

       fi

10.7.3

       case var in

               patter1)

                       commands

                       ;;

               patter2)

                       commands

                       ;;

               patter3)

                       commands

                       ;;

               ......

       esac

第11章高级shell编程

11.1 算数和逻辑操作

11.1 算数和逻辑操作

11.1.1 显式模式的let命令

11.1.2 隐式模式的let命令

11.2 while-do-done loop

**11.2 while-do-done**

       while condition(条件为真,循环继续)

       do

               command block

       done

_Example:_

#!/usr/bin/sh -x

echo &quot;Please input:&quot;

read VAR

#while [ $VAR **-lt** 100 ]

while (( $VAR **&lt;** 100 ))

       do

       echo &quot;THE VAR is $VAR.&quot;

#       let VAR=VAR*2

        ((VAR=VAR*2))

done

11.3 until-do-done loop

**11.3 until-do-done**

       until condition(条件为假,循环继续)

       do

               command block

       done

_Example:_

#!/usr/bin/sh -x

echo &quot;Please input:&quot;

read VAR

until  (( $VAR **&gt;** 100 ))

       do

       echo &quot;THE VAR is $VAR.&quot;

        ((VAR=VAR*2))

done

11.4 for-do-done loop

11.4 for-do-done 循环

       for VAR in list

       do

               command block

       done

**_EXAMPLE:_**

_#!/usr/bin/sh_

for VAR in ~/*

do

       [ -x $VAR ]

       ls -lia $VAR

done

11.5终端一个循环

11.5.1 break

       break命令跳出循环到done后面的命令.可以使用break -n 指导直接跳转到done后面第n调命令.

**Example:**

#!/usr/bin/sh

while [ 1 -eq 1 ]

do

       echo &quot;Please input a file name:&quot;

       read FILE

       if [  -x $FILE ]

               then

               echo &quot; The file  $FILE is exsist!&quot;

                        **break**

       else

               echo &quot;THE file $FILE is not exsist!.&quot;

       fi

done

echo &quot;BYE&quot;

11.5.2 continue

       continue 跳过循环的剩余部分,再次继续循环

**Example:**

#!/usr/bin/sh

while [ 1 -eq 1 ]

do

       echo &quot;Please input a file name:&quot;

       read FILE

       if [  -x $FILE ]

               then

               echo &quot; The file  $FILE is exsist!&quot;

               continue

               echo &quot;Thanks for you corperation!&quot;

       fi

done

echo &quot;BYE&quot;

11.5.2 exit

       exit完全退出当前程序,并且可以指定退出代码

Example:

#!/usr/bin/sh

NUM=100

while [ 1 -eq 1 ]

do

       echo &quot;Please input a divsion for integer 100:&quot;

       read DIV

       if [ $DIV -eq 0 ]

               then

               echo &quot; Divide by zero is mot permitted!&quot;

               exit 1001

       fi

       let QUO=NUM/DIV

       let REM=NUM%DIV

       echo &quot;QUO is $QUO&quot;

       echo &quot;REM is $REM&quot;

done

echo &quot;BYE&quot;

11.6文本处理

11.6.1 sed

       $sed /s/ECHO/echo/g #

11.6.2 cut

11.6.3 sleep

第2篇 HP-UX系统管理

第12章 系统管理

SAM

root@cschp87 # sam

Starting the terminal version of sam...

To move around in sam:

- use the &quot;Tab&quot; key to move between screen elements

- use the arrow keys to move within screen elements

- use &quot;Ctrl-F&quot; for context-sensitive help anywhere in sam

On screens with a menubar at the top like this:

       ------------------------------------------------------

      |File View Options Actions                         Help|

      | ---- ---- ------- ------------------------------- ---|

- use &quot;Tab&quot; to move from the list to the menubar

- use the arrow keys to move around

- use &quot;Return&quot; to pull down a menu or select a menu item

- use &quot;Tab&quot; to move from the menubar to the list without selecting a menu item

- use the spacebar to select an item in the list

On any screen, press &quot;CTRL-K&quot; for more information on how to use the keyboard.

Press &quot;Return&quot; to continue...

第13章 安装HP-UX

13.1

700/800

入门                 9000 L/A/R

中小企业        9000 K/N

大型企业        9000 V

第14章 系统启动和关闭

14.1 引导过程介绍

14.2 处理器相关代码

14.2.

14.2.1 PDC 菜单

14.2.2 搜索引导设备

boot P6 或者

boot 10/4/4.2

14.2.3 从预备设备引导

14.2.4 稳态存储器

14.2.5 引导到单用户模式

14.3 系统磁盘上的引导区

14.4 初始化系统加载器

14.5 装载HP-UX内核

14.5

14.5.1 swapper进程

       该进程的PID为0,管理换入换出的内存.

14.5.2/sbin/pre_ini_rc:

       该文件包含fsck命令,用于在启动过程中检查文件系统.

14.6 ini进程

14.6 init 进程

**14.6.1 /etc/inittab**

14.7 运行级别

14.7

14.7.1 改变运行级别

       #init [0-6]

14.7.2判断当前的运行级别

       # who -r

         .       run-level 3  Oct 27 22:26    3    0    S

14.8 添加在引导式运行的程序

启动和关闭脚本位于; /sbin/init.d/

14.8.1 定序器目录

ln -s /sbin/init.d/ /sbin/rcX.d/

/sbin/rcX.d/

14.8.2 配置文件/etc/rc.cofnig.d/

14.9 关闭系统

shutdown

-r        

-h

-y

14.9.1 关闭和重启命令

reboot 关闭所有进程而不是安全的终止他们。可能活引起数据丢失。

14.9.2 shutdown.allow 文件

格式：

系统名 用户名

第15章 软件和补丁管理

SD-UX （Software Distributor）

Software selections are specified as:

   product[.subproduct][.fileset][,version] ...

15.1软件包结构

bundle[.product][.subproduct][.fileset][,version] ...

在SD-UX中软件被组织成一个部件或对象的层次结构。

这些部件是文件集、子产品、产品和包。

这些部件的存储位置叫做软件仓库。

文件集：一个文件集是文件和一些控制脚本的集合，是软件包层次结构中基本的条目。一个文件集只能属于一个产品但是它可以包含在很多子产品和包中。

子产品：如果一个产品包含多个文件集，最好把逻辑相关的文件集组合到一个子产品中。一个文件集可以是多个子产品的成员。

产品：        产品是文件集和（或）子产品的超集。缺省时，SD-UX用于处理产品。

包：        包一般由HP-UX打包用于软件的发布。包包含属于不同产品的文件集。一个产品不必再一个包中，因为包可以有不同产品的部分。与软件维护相关的操作可以在包上作为一个条目来完成。

软件仓库：软件仓库是文件集、产品和包的存放位置。一个软件仓库可以是用于发布软件的磁盘上的目录，如一个CD-ROM或磁带。缺省的软件仓库目录是/var/spool/sw。可以使用任何一个目录作为软件仓库，同一个服务器上为不同的应用程序提供多个软件仓库是可能的。

HP-UX提供四種不同程度的包裝方法：

Bundle: 提供特定功能的一群fileset僅限於HP-UX上使用。

Product: 由sub-product、fileset 和檔案 (file)所組成，系統管理者可以利用SD-UX的指令，自行將軟體包裝成product

sub-products: 由fileset所組成，屬於某一product。

filesets: 由檔案成組成，SD-UX軟體管理的最小單位。

15.2 列出已安装的软件

swlist 用于列出软件。

swlist -l bundle        只列出包

swlist -l product        只列出产品

swlist -l fileset        列出文件集

swlist -d @ /var/spool/sw        列出软件仓库.var/spool/sw中的软件

swlist -l file X11                列出所有X11产品中的文件

swlist -d @ hp1:/mydepot        列出主机hp1上名为mydepot的软件仓库中的软件

swlist也可以用于列出大小，修订本和开发商信息等属性。

15.3 安装新的软件

swinstall 用于软件安装。

根据你的终端类型，这个命令在文本或者图形接口中启动。

如果你想从一个特定的软件仓库安装，可以在命令行借助-s开关声明软件源。

例如，为了从一个磁带驱动器安装软件：swinstall -s /dev/rmt/0m

**15.3.2安装/升级日志文件**

swinstall命令的所有动作都被记录在/var/adm/sw/swinstall.log文件中。

日志文件中包括一些标志：

=======        表示一个任务的开始和或结束

ERROR                表示了一个导致不可能安装的严重错误

WARNING        表示虽然安装完成，但可能有一些错误

NOTE                所有信息都放在这个标志下。大多数时候可以忽略这些消息

**15.3.3 使用代码字安装受保护的软件**

一组匹配的：Customer ID and CodeWord

代码字被保存在/var/adm/sw/.codewords

**15.3.4 SD-UX守护进程和代理**

守护进程：swagentd

代理进程：swagent

如果这个守护进程没有运行，就不能开始软件的安装过程。

SD-UX守护进程在运行级2启动，如果你在一个单用户模式，就不能安装软件。

但可以使用命令启动守护进程：

/sbin/init.d/swagentd start

关闭守护进程：

/sbin/init.d/swagentd stop

**15.3.5 已安装产品数据库**

HP-UX维护一个所有已安装软件的数据库（IPD）。

在分析阶段，swinstall使用这个数据库赖检查已安装的软件，swlist列出已安装软件。

swremove命令删除时，这个数据库升级来反映被删除的软件。

SD-UX命令负责维护这个保存在/var/adm/sw/products目录结构中的数据库。

15.4 删除软件

swremove命令用于从HP-UX系统删除软件。

它有着和swinstall相同的界面。

一旦软件删除开始，SD-UX检查相关的软件并删除所有在被选择的软件中且没有被其他任何产品和包使用的文件。

它通过删除软件来更新PID。

只通过删除软件所在目录并不能删除该软件，事实上，手工地删除这个目录可能导致问题。因为软件条目始终保持在PID中，尽管你已经删除了这个文件，但是系统认为它们仍然存在。当SD-UX检查相关软件时可能影响其它软件安装或删除过程。

软件的删除过程记录在/var/adm/sw/swremove.log文件中。

**查找并删除无用的文件集：**

freedisk命令用于列出并删除已经很长时间没有使用的软件。在分析了文件集之后，该命令激活swremove命令来交互地删除包。

15.5确认已安装的软件

swverify 命令用于确认一个安装在系统中或软件仓库中的软件。

它检查文件的存在性和完整性及在一个软件包中的附属文件。包也执行软件提供的脚本来确认软件的完整性。

当使用-d时，它操作一个软件仓库而非一个已安装软件。

如果软件确认成功它返回一个等于0的代码。

这个命令的日志记录在/var/adm/sw/swverify/log，它可以检查任何错误消息。

15.6 管理软件仓库

管理软件仓库：

大型网络通过建立软件仓库避免在每台机器上使用安装安装介质。

软件仓库可以在磁盘上任何目录中创建。缺省软件仓库的位置是：/var/spool/sw。

磁带软件仓库可以使用swpackage命令创建。每次只能有一个命令可以访问磁带软件仓库。

swcopy -s /dev/rmt/0m @ /var/spool/sw       从一个磁带驱动器拷贝所有的产品到缺省软件仓库

swremove -d * @ /var/spool/sw               从缺省的软件仓库中删除所有软件

swlist -d @ /dev/rmt/0m                     列出本地磁带中的内容

15.7 HP-UX补丁

HP-UX 补丁：

给HP-UX操作系统或产品添加新的功能

添加对新硬件的支持

修补操作系统和应用程序的漏洞

补丁文件由PH开头，后面两个字符表示补丁类型：

**15.7.1 补丁源**

**15.7.2 补丁类型**

命令补丁：其类型字段为CO

内核补丁：其类型字段为KL

网络补丁：其类型字段为NE

子系统补丁：其类型字段为SS（包括其他类型的补丁）

例如:PHCO_16423

**15.7.3 列出已安装的补丁**

swlist -l product PH*                                         #HP-UX 10.x

swlist -l patch &amp;apos;*.*,c=patch&amp;apos;   或 swlist -l patch            #HP-UX 11.00

15.8 安装和删除补丁

15.8.1 获取补丁

[http://www11.itrc.hp.com/service/patch/mainPage.do](http://www11.itrc.hp.com/service/patch/mainPage.do)

$sh PHCO_15220 #unshare 该补丁包

PHCO_15220.txt

PHCO_15220.depot

Patch_Name.txt   #补丁描述文件

Patch_Name.depot #补丁文件

.txt包含如下信息：

补丁名

补丁描述

生成日期：显示补丁的生成日期

发布日期：显示补丁的发布日期

硬件平台：OS版本

产品

文件集

自动重启：描述在安装完补丁后是否会自动重启

状态：显示是否是一个常规版本或者特殊版本

严重性：显示该补丁是否修复了一个严重问题。

类别标签

路径名：显示在网络上的文件路径

缺点描述

SR：服务请求号

补丁文件

what(1) 输出：显示每个文件的what命令输出

cksum(1)输出：检测文件中的错误

补丁冲突

相关的补丁

相关的硬件

其他的相关

取代

等同的补丁

安装说明

**15.8.2 生成补丁仓库**

unshare一个补丁之后：

1.直接安装.depot文件

2.把.depot加入到系统的补丁仓库

生成补丁仓库：swcopy -s PHCO_15520.depot PHCO_15520 @ /var/spool/sw

**15.8.3 安装补丁**

swinstall -s /var/spool/sw

会得到一个所有补丁列表

From CD-ROM：

HP-UX 10.20以前需要手动 mount /dev/CD-ROM /SD_CDROM

HP-UX 11.0 CD-ROM有swinstall自动挂载

**15.8.4 删除补丁**

swremove

15.9 SD-UX命令

SD-UX 命令总结：

swinstall        安装软件

swremove        删除已安装软件;从仓库中删除软件

swlist                列出所有已安装或在仓库中的软件

swcopy                拷贝软件部件到软件仓库

swpackage        打包仓库中的软件

swreg                使软件仓库对于网络上的其他系统可见

swverify        确认已安装软件的完整性

swagentd        SD-UX守护进程

swagent        SD-UX代理

swacl                控制对软件的访问

swconfig        配置已安装的软件

第16章重新配置HP-UX内核

缺省的HP-UX内核以vmunix为名保存在/stand目录中。

内核配置是一个添加或删除驱动程序或子系统之后重新生成内核的过程。

HP-UX配备了在/usr/conf目录中提供的被支持的设备驱动程序和子系统。对新设备的支持通过内核补丁来提供。安装内核补丁需要重建内核。

内核重建分三个步骤：

1.内核配置文件/stand/system

16.1 为什么要重新配置内核

SD-UX 在安装完内核相关的补丁后会自动重新配置内核。

16.1.1 添加或删除设备驱动程序

16.1.2 添加或删除子系统

16.1.3 改变交换和转储设备

16.1.4 修改系统参数

16.2 重新配置过程

HP-UX内核可以使用命令行或者SAM来配置。

**16.2.1 准备新的系统配置文件**

       内核配置文件 /stand/system

       #system_prep        #用来生成

       #sysdef                #查看现有内核参数

在添加和删除设备之前应该查看一下

连接到系统上的硬件列表（驱动程序）：

#iosacn -f

子系统（如网络子系统）：

#lanscan

生成新的配置文件步骤：

1\. #cd /stand/build

2\. 生成当前系统文件

/usr/lbin/sysadm/system_prep -s system

一个典型的系统文件包含以下三个部分：

drivers and subsystems

kernel device info

Tunable parameters

16.2.2 编译内核

/usr/sbin/mk_kernel -s /stand/build

mk_kernel 命令使用/usr/conf目录中的主要程序和库文件。想要附加模块文件在/stand/system.d目录中。

新的内核可执行文件以vmunix_test命令创建在/stand/build目录中。

16.2.3 安装新内核和配置文件

备份旧的内核和系统的文件

        mv /stand/vmunix /stand/vmunix.old

        mv /stand/system /stand/system.old

安装新的内核

        cp /stand/build/system /stand

        cp /stand/build/vmunix_test /stand/vmunix

16.3 在shell 中重建内核

在shell中使用如下步骤完成内核重建过程：

（1）改变目录到/stand/build

        cd /stand/build

（2）从运行的系统中生成内核参数系统文件

        /usr/lbin/sysadm/system_prep -s system

（3）编辑内核系统文件来做必要的修改

        vi system

（4）使用mk_kernel命令生成新的内核

        /usr/sbin/mk_kernel -s ./system

（5）备份旧的内核和系统的文件

        mv /stand/vmunix /stand/vmunix.old

        mv /stand/system /stand/system.old

（6）安装新的内核

        cp /stand/build/system /stand

        cp /stand/build/vmunix_test /stand/vmunix

（7）重新引导系统

        shutdown -r 0

（8）确认修改了的参数和附加的设备

        sysdef               #查看系统可调的内核参数值

        ioscan               #查看连接到系统的硬件列表

16.4 从旧的内核引导

16.5 常用内核可调参数

第17章外部设备

HP-UX 通过/dev目录下的设备文件与所有的设备通信。

这些设备文件不同于普通的磁盘文件，它们不占用任何磁盘空间。

只要数据写入这些设备文件中，它们都被送到了这个文件代表的设备。

例如：你输入一些数据到一个打印机设备文件，它们就连接到一台打印机来完成打印过程。

大多数设备文件由HP-UX自动创建。在引导过程中，HP-UX探测所有设备并且在需要的时候执行/sbin/ioinit.rc脚本来创建新的设备文件。

HP-UX提供手工创建设备文件的命令。

在系统启动的时候，内核会执行一系列系统初始化的工作，包括探测所有的安装在系统中的硬件。在进行硬件探测的时候，内核会确认所有的设备－总线，适配器，设备适配器－这些能够被自动配置的设备。内核绑定一个合适的驱动程序给每一个检测到指定硬件地址的设备。

在完成系统初始化后，内核执行init命令。init进程读取/etc/inittab文件来激活几个系统启动的命令，包括/sbin/ioinitrc。

第一步,initrc会读取/etc/ioconfig文件的内容，并将在那里找到的设备对照信息转换成内核数据结构io_tree。

下一步，ioinit执行insf。insf会为新的设备创建设备文件。它同样会更新/etc/ioconfig文件和内核树。

17.1 设备和物理路径

**17.1 设备和物理路径**

所有HP-9000系列服务器和工作站使用PA-RISC处理器。

处理器用总线连接多种类型的设备适配器。

所有的设备连接到这些设备适配器上。

在HP系统中使用的总线有：

扩展的工业标准架构（EISA）

通用系统连接（GSC）

Hewlett-Packard精确总线（HP-PB）

高速系统连接（HSC）

PCI

每一种总线有它自己的特性，如时钟频率、数据传送和信号。

**17.1.1 常用设备适配器**

1.SCSI（小型计算机系统接口）适配器：

用于连接磁盘驱动器、磁带驱动器和CD-ROM驱动器

标准SCSI适配器支持7个设备，每秒传送5M字节，设备号优先级6-0递减。

Fast/Narrow或差动SCSI同样支持7个设备，每秒传送10M字节，设备号优先级6-0递减。

Fast/Wide SCSI适配器支持15个设备，每秒传送20M字节，设备号优先级6-0、15-8，6最高，8最小。

所有的SCSI设备必须在系统启动前加电并且在系统关闭后断电。

不能从一个正在运行中的系统中连接或拔下设备。

2.多路转接器（MUX）：

用于把串行设备连接到系统中。

通常它用于连接modem、终端和任何串行绘图仪或打印机。

3.LAN卡

**17.1.2 硬件路径：**

一个硬件路径表示了一个系统中一个设备的位置。

例：一个路径为8/12.5.0表示一个SCSI磁盘连接到系统。

数字8表示系统的一个总线号

数字12表示SCSI适配器在总线上的地址

数字5为SCSI的设备号（优先级）

数字0为lun,逻辑单元号

一个硬件地址8/5/0表示一个光纤适配器连接到总线8，总线转换器5，设备号为0

在HP-9000服务器背板上，你可以看到扩展槽上面便有这些数字。

为了列出系统中的这些设备，使用ioscan命令。

#ioscan -fC disk

Class      I        H/W Path         Driver         S/W State       H/W Type         Description

===================================================================

disk         6      10/4.8.0            sdisk           CLAIMED         DEVICE          SEAGATE ST34371W.....

disk         5      16/5.2.0            sdisk           CLAIMED         DEVICE          TOSHIBA CD-ROM XM-5401TA......

其中命令输出域的含义：

Class           显示设备的分类

I               实例，存在多个同类设备时，通过实例号区分。

H/W  Path       硬件路径

Dirver          控制设备的驱动程序名

S/W State       CLAIMED意味着设备驱动程序被装入了内核而且绑定到了该设备

               UN-CLAIMED意味着这个设备的驱动程序在内核中不存在      

H/W Type        显示设备的类型

Description     对设备的简短描述

17.2 设备文件

**17.2 设备文件**

在HP-UX中每一个设备在/dev目录中有一个相应的设备文件。

这个文件描述了设备的硬件路径并且用于与该设备通信。

这些设备文件由HP-UX自动生成，不包含任何数据。

**17.2.1 设备目录的层次**

用于组织设备文件的目录

/dev/dsk                         磁盘驱动器和CD-ROM的块设备文件

/dev/rdsk                        磁盘驱动器和CD-ROM的字符设备文件

/dev/vg00                        卷组vg00设备，每一个卷组都有自己的目录

/dev/rmt                         磁带驱动器的设备文件

/dev/pts                         基于流的伪终端设备文件

/dev/pty                         伪终端次设备文件

/dev/ptym                        伪终端主设备文件

**17.2.2 主号和次号**

使用ll命令列出部分设备文件：

brw-r----- 1 root sys  31  0x005000 Feb 10 1997  /dev/dsk/c0t5d0

brw-r----- 1 root sys  31  0x006000 Feb 10 1997  /dev/dsk/c0t6d0

crw-r----- 1 root sys  31  0x005000 Feb 10 1997  /dev/rdsk/c0t5d0

crw-r----- 1 root sys  31  0x006000 Feb 10 1997  /dev/rdsk/c0t6do

crw-r----- 2 root tty  17  0x000001 Jan 9　09:25 /dev/ttyp1

crw-r----- 2 root tty  17  0x000002 Jan 9　17:25 /dev/ttyp2

没有显示文件大小，相反，第5和第6字段还有一些其他信息。

第5字段代表主设备号，表示该设备的内核驱动程序。所有相同类型的设备有同样的主设备号。

第6字段代表次设备号，显示一个设备的物理地址。用来区分相同主号的设备。

**17.2.3 字符设备与块设备**

字符设备也成为原始设备，这些设备的I/O每次都被格式化为1个字符。这些设备用于串行数据传输。这类字符设备有终端、modem、串行打印机和磁带驱动器。对于这些设备文件，ll每一行的第一个字符输出是c。

**17.2.4 块设备**

块设备用于从（向）一个设备传输一个数据块。数据通过内存一个缓冲区进行交换。所有的磁盘驱动器和CD-ROM驱动器都是块类型设备。ll每一行输出的第一个字符是b。

磁盘驱动器上也有字符设备文件。

17.3 SCSI设备文件命名

**17.3 SCSI设备文件命名**

SCSI设备文件在HP-UX中遵循一个通用的命名规则。（这些文件可以自己指定其他名字）

模式：c# t# d#[....]

c#表示接口卡和指定给这个卡的实例号。

t#表示SCSI的目标地址，目标地址表示SCSI总线上的设备号。

d#是逻辑单元号，通常为数字0

[...]是可选的与设备相关的信息

**17.3.1 磁盘命名**

**17.3.2 磁带设备**

磁带设备也遵循与磁盘设备相同的命名规则，然而，根据磁带盒的类型与它的格式，一个其他可选功能的数字也包含在设备名中。

tape   1    10/8.1.0   stape    CLAIMED     DEVICE     IBM ULTRIUM-TD3

                                 /dev/rmt/1m             /dev/rmt/c15t3d0BEST

                                 /dev/rmt/1mn           /dev/rmt/c15t3d0BESTn

                                 /dev/rmt/1mb           /dev/rmt/c15t3d0BESTb

                                 /dev/rmt/2mnb         /dev/rmt/c28t3d0BESTnb

设备文件中的单词&quot;BEST&quot;表示使用尽可能最高的容量格式。

字符&quot;n&quot;表示在操作结束后磁带不会回卷。

字符&quot;b&quot;表示磁带驱动器将采用Berkely类型替代AT&amp;T。

在HP-UX10.X版本之前，一个不同的命名规则用于磁带设备。

例如，磁带设备名是/dev/rmt/0m，/dev/rmt/1m等等。在这个格式中，一个阿拉伯数字后面跟着一个字符&quot;m&quot;用于磁带设备这个数字后面跟随附加字符表示设备属性。例如/dev/rmt/c15t3d0BESTn可以用/dev/rmt/1mn表示。这个命名规则用于向后兼容性。ioscan -funC tape命令输出显示了两种设备。

17.4 列出已安装的设备

**17.4 列出已安装的设备**

**17.4.1 使用ll命令**

   brw-r----- 1 root sys 31 0x005000 Feb 10 1997 /dev/dsk/c0t5d0

   brw-r----- 1 root sys 31 0x006000 Feb 10 1997 /dev/dsk/c0t6d0

   crw-r----- 1 root sys 31 0x005000 Feb 10 1997 /dev/rdsk/c0t5d0

   crw-r----- 1 root sys 31 0x006000 Feb 10 1997 /dev/rdsk/c0t6do

可以显示出一个设备文件的如下特征：

文件类型

第5字段的主号

第6字段的次号

17.4.2 使用ioscan命令

有一个超过ll命令的优点，即表示哪个设备文件连接到什么设备。

root@cschp87 #  ioscan -funC disk

Class     I  H/W Path      Driver S/W State   H/W Type     Description

======================================================================

Class：设备类型

I：设备实例号

H/W Path：设备硬件路径

Driver：设备内核驱动程序

S/W State：表示驱动程序是否连接到了设备

描述域显示了设备是什麽类型。

它也可以用于显示一个特定类型设备相关的设备文件。

    比如：

    ioscan -funC disk                 #只列出磁盘类设备与它们相关的设备文件名

    ioscan -fun                           #列出设备与它们相关的设备文件名

    ioscan -funC tape                 #只列出磁带类设备与它们相关的设备文件名

    ioscan -funcH 2/0/1.6.0        #只列出在2/0/1.6.0的设备文件

17.4.3 使用lssf命令

   显示每一个设备文件的特征。

   # lssf /dev/rmt/0mn

　　tape2 card instance 1 SCSI target 0 SCSI LUN at@t no

　　rewind best density available at address 52.0.0 /dev/rmt/omn

     这个输出显示了ioscan没有提供的附加信息，它还显示了：

     设备文件使用哪种驱动

     设备的硬件地址

     所有被设备文件使用的与设备有关的访问方式

**17.4.4 可用设备**

ioscan -u #是显示可用的设备

17.5 生成设备文件

**17.5.1 自动配置**

当在系统上安装HP-UX时，设备文件被自动生成。之后，每次你引导系统，HP-UX扫描所有连接的设备，如果该设备是自动配置的，则生成设备文件。但需要亲自为不能自动配置的设备生成设备文件。

**17.5.2 使用insf命令**

infs命令为新的设备生成设备文件，它的引导过程自动执行。也可以用它生成附加的设备。

Insf的选项：

-d           通过设备文件名选择特殊的设备

-C           与制定分类匹配的设备，如磁盘，终端等

-H           与指定硬件路径匹配的设备

-I           选择板卡实例

-e           为已经存在的设备创建或重建设备文件

-D           覆盖默认设备安装目录或目录中安装的指定文件，目录必须存在

-d、-H和-C选项用以指定驱动器、设备类型或硬件路径地址来选择设备。

可以用lsdev命令确定内核中的驱动和类别；用IOSCAN命令列出内核中的硬件路径。

例如：insf -C disk              #生成磁带驱动器的设备文件

          insf -C tape -e         #生成磁带驱动器的设备文件，即使文件已存在。

          insf -H 0.1.0 -e        #重新生成硬件路径为0.1.0的设备文件

          insf -e -n 100 -d ptym        #创建100个伪终端

**17.5.3 使用mksf命令**

如果系统已经发现了某个设备，则可以用mksf命令来创建设备文件。

mksf选项：

-d           通过设备文件名选择特殊的设备

-C           与制定分类匹配的设备，如磁盘，终端等

-H           与指定硬件路径匹配的设备

-I           选择设备实例

-D           覆盖默认设备安装目录或目录中安装的指定文件，目录必须存在

为已经存在的设备创建自定义的设备文件之前，可以用ioscan查找板卡的实例号。

mksf -d tape2 -I 0 -b DDS1          #为磁带驱动器创建字符设备文件/dev/rmt/c0t0d0DDS1

mksf -C printer -I 2 /dev/printer    #创建设备文件/dev/printer，并映射行式打印机

**17.5.4 使用mknod命令**

mknod命令可以用于生成字符设备文件、块设备文件或代表命名管道的文件。

为了生成字符或块文件，必须在命令行声明主和次号。

mknod /dev/rmt/0m c 212 0x030080      #为主号212次号0x030080的磁带驱动器生成字符设备文件

17.6 安装一个新设备

**17.6 安装一个新设备的步骤：**

（1）如果用于该设备的设备驱动文件已经安装在内核中，跳到下一步。

    如果设备驱动程序没有在内核中生成，重新配置内核以包含该设备驱动程序。

（2）关闭系统，关闭电源并安装该设备。

（3）重新引导系统。

（4）HP-UX内核将扫描新的硬件设备并在启动过程中安装新设备。

（5）在系统启动之后，以ROOT登录并使用ioscan命令确认该设备已被检测到，并且设备文件已经安装。

    如果文件没有安装，使用已经学习过的命令安装设备文件。

17.7 终端和modem

终端和modem：

终端和modem是串行设备并且被连接到一个串口或一个MUX上。

它们没有专用的目录，设备文件直接放在/dev目录下面，没有子目录。

它们的设备文件不遵循c#t#d#命名规则。

每一个终端设备文件由tty开头后面跟着一个MUX号，下一个字母是&quot;p&quot;跟一个MUX上的端口号。

例如：/dev/tty0p3表示终端在第一个MUX的端口3上。

伪终端设备文件被使用终端模拟和网络服务的应用程序使用，由主副文件成对出现。

伪终端设备主文件在/dev/ptym，副文件为/dev/pty。名字都为pty开头。链接到/dev下的同名文件。

基于流的伪终端设备文件保存在/dev/pts中。

缺省提供60个伪终端设备文件，通过insf -e -n 90 -d ptym创建90个伪终端设备文件。

完整功能的modem由3个设备文件表示。

例子：

对于链接到第一个MUX端口4上的Modem的设备文件是：

/dev/cua0p4

/dev/cul0p4

/dev/ttyd0p0

第18章 HP-UX文件系统和逻辑卷管理

磁盘和文件的系统管理是一项重要的系统管理任务。它包括添加和删除磁盘、配置磁盘、基于某种配置生成和管理文件系统和磁盘问题的修复。

18.1 磁盘设备和相关配置

**18.1 磁盘设备和相关配置**

每个物理磁盘都有两个相关的设备文件，一个是字符设备文件，一个是块设备文件。

每一个磁盘在被系统使用之前都必须经过配置。

一个磁盘可以被细分为多个部分组成，这些部分可能是：

一个引导区：特殊区域，包含系统启动时所必须的程序及文件等

文件系统：存储文件的空间，比如/usr、/var或/home等，可以有多个文件系统

一个交换区：作为交换空间，也作为崩溃转储

原始数据区：储存原始数据，比如数据库的数据

HP-UX提供了两种磁盘管理的方法：

18.2 逻辑卷管理介绍

**18.2.1 整盘分区**

一个磁盘可以配置成以下5中方式：

单独的一个文件系统

完全用作交换区

完全用作原始数据区（raw data）

一个磁盘同时包含文件系统和交换区

一个磁盘配置成为启动盘，包含根文件系统、交换区和2M的特殊启动区域

不足：

每个磁盘只能有一个文件系统分区。

文件系统也不能扩展到多个磁盘。

当后期需要更多空间时，扩展文件系统很难。

**18.2.2 逻辑卷管理磁盘分区**

物理卷：实际的物理磁盘驱动器。使用pvdisplay命令显示物理卷。

卷组：  多个物理卷组合成一个卷组，它将所有物理卷的空间融合成一个独立的实体。第一次安装HP-UX，默认生成一个根卷组名为：/dev/vg00。使用vgdisplay 显示。

逻辑卷：由一个或多个物理卷构成，在卷组中创建并可以跨越多个物理卷。对于逻辑卷，你可以任何时候根据需要去改变它的尺寸而不丢失数据。使用lvdisplay命令显示逻辑卷。

逻辑卷管理使你能将几个磁盘（物理卷）里的空间组合成一个卷组。然后把卷组里的空间再划分成逻辑卷。逻辑卷克服了整盘方法的一些不足，可以实现以下功能：

创建跨越多个磁盘的逻辑卷

在同一磁盘上创建多个逻辑卷

根据需要扩展和压缩逻辑卷

卷组设备文件为/dev/vg00/group。

每一个逻辑卷组中都有两个设备文件，字符与块。

所有lvm设备文件的主号为64次号显示了逻辑卷名跟逻辑卷组之间的成员关系。

18.3 列表显示和创建逻辑卷

物理扩展（PE）：是最小的磁盘空间分配单元，缺省为4M。

逻辑扩展（LE）：是内核内存中指向磁盘上某一个PE的指针。

PE的大小在创建卷组时背固定，整个卷组中的PE都是一样的。

为了扩大逻辑卷，LVM只需要分配更多的LE。

**18.3.1 列表显示物理卷**

# pvdisplay /dev/dsk/c1t6d0

--- Physical volumes ---

PV Name                     /dev/dsk/c1t6d0

VG Name                     /dev/vg00

PV Status                   available

Allocatable                 yes

VGDA                        2

Cur LV                      11

PE Size (Mbytes)            4

Total PE                    4340

Free PE                     208

Allocated PE                4132

Stale PE                    0

IO Timeout (Seconds)        default

Autoswitch                  On

该磁盘所属的卷组名vg00

当前他给11个逻辑卷分配了空间

物理单元的尺寸4MB

该磁盘所包括的PE总数为4340

在4340个PE中，4132个PE已经分配，208个空闲。

**18.3.2 列表显示卷组**

# vgdisplay /dev/vg00

--- Volume groups ---

VG Name                     /dev/vg00

VG Write Access             read/write

VG Status                   available

Max LV                      255

Cur LV                      11

Open LV                     11

Max PV                      16

Cur PV                      2

Act PV                      2

Max PE per PV               4350

VGDA                        4

PE Size (Mbytes)            4

Total PE                    8680

Alloc PE                    8264

Free PE                     416

Total PVG                   0

Total Spare PVs             0

Total Spare PVs in use      0

此卷组最多可见255个逻辑卷

当前卷组中有8个逻辑卷

该卷组最多可包含16个物理卷

当前卷组中包含2个物理卷

每个物理卷最多包含4350个PE

一个有8680个物理单元，8264个已被分配，416个空闲。

**18.3.3 列表显示逻辑卷**

18.3.4 创建物理卷

创建物理卷是LVM管理磁盘的第一步，为了找出某个磁盘相关的设备文件，使用IOSCAN命令。

也许你想查看磁盘的大小，可以使用diskinfo命令完成。

在创建之前，先通过mediainit命令对一个磁盘进行格式化和校检其完整性。

创建物理卷：

首先格式化硬盘：mediainit /dev/rdsk/c2t5d0                  #后面的参数必须为字符设备文件

创建物理卷：pvcreate /dev/rdsk/c2t5d0

若磁盘已经属于某个卷组，可以用-f选项强制执行创建（慎用）。

建好卷组后，可以通过pvdisplay命令来检查它。（没有成为卷组前不能pvdisplay）

LVM使用的数据结构会造成一些磁盘空间的开销。

非启动盘上如果设置了较小的PE或创建了很多物理卷，则LVM数据结构将会比较大。

这个开销在可启动的LVM盘上是固定的（2912KB）。

18.3.5 创建卷组

建完物理卷后，就可以将它添加到卷组中。

1.首先在/dev目录下面创建一个卷组名为vg03的目录：mkdir /dev/vg03。

2.在该目录下面创建卷组设备文件，主号为64，次号显示组名：

 mknod /dev/vg03/group c 64 0x030000

4.最后用vgcreate命令创建卷组，以物理卷名为参数：

vgcreate /dev/vg03 /dev/dsk/cdt5d0

关于vgcreate的一些选项：

-l                   卷组最大能包含的逻辑卷数，默认为255

-p                  卷组最大能包含的物理卷数，默认为16

-e                  卷组中每个物理卷最多能包括的PE数，默认为1016

-s                  卷组中物理单元的尺寸大小，默认为4

建好卷组后，可以通过vgdisplay命令来检查它。

**18.3.6 创建逻辑卷**

包含所有或任何一部分物理卷上的空间

扩展到多个LVM物理卷

如果需要，可以改变大小，移动到不同磁盘中

可以使用任何你需要的命名规则，默认是：/dev/vg**/lvol [1..2..3...]

用lvcreate命令可以创建逻辑卷。

当逻辑卷新创建时，其相应的字符设备及块设备文件会在卷组目录下生成。

例如：为了在卷组vg03中创建一个空间为800M，名为moko的逻辑卷：

lvcreate -L 800M -n moko vg03

关于lvcreate命令的选项：

-L              以MB为单位表示逻辑卷的大小，默认为0

-l               以逻辑单元的数目来表示逻辑卷的大小，默认为0

-n             逻辑卷名称，若不指定，默认的名为lvol1,lvol2...

-C             用临近的空间来创建逻辑卷

-i               设定可以被逻辑卷使用的磁盘

-I               当逻辑卷使用一个以上的磁盘时，设定穿过每个物理卷的条带尺寸，i与I必须一起使用

**18.3.7 LVM数据结构**

卷组所包含的每一个磁盘都有LVM的数据结构：

物理卷保留区（PVRA）：由pvcreate命令创建，含有物理卷信息

卷组保留区（VGRA）：由vgcreate命令创建，包含卷组状态区（VGSA）和卷组描述区(VGDA)，用于卷组的设备驱动信息。

坏块重新分配区域（BBRA）：由pvcreate创建，它是磁盘尾部的一个区域，发现物理卷缺陷时由LVM使用。

18.4 文件系统介绍

文件系统时将文件和目录一起存储的集合。

分配给文件系统的区域被分成两个主要部分，即用户区和元数据区。

用户区用于存储用户文件中真正的数据。

元数据区存储文件系统的结构数据：

超级块：包含文件系统类型，尺寸信息，还有指向元数据结构的指针

I节点：保存文件属性的记录。比如文件属主，权限，类型等。02总是代表根目录。

目录：目录区保存文件名与之相关的I节点的记录。

**18.4.1 文件系统类型**

**高性能文件系统（HFS）：**

传统的HP-UX文件系统，作为/stand的文件系统。

所有HFS文件系统的前8KB空间用作HFS主超级块，包含一般的文件系统信息。

超级块还包含指向文件系统中所有其他HFS结构数据的指针。

HFS拥有多个超级块备份，位置在/var/adm/sbtab。

被损坏的HFS超级块通过这些备份进行修复。

在一个读请求中，HFS块是最小数据单元，缺省为8KB大小，有效数据块为4-64K，2的乘方。

段是用于分配的最小数据单元，HFS块可以分成多个段。

HFS便于管理，然而不能缩减它的空间，也不能方便地扩展空间，扩展前必须卸载文件系统。

当创建HFS文件系统时，必须标明你需要创建多少I节点。

I节点存放在新文件系统的I节点表中。

如果没有空闲的I节点，即使你有空闲的数据块，也不能创建新文件目录。

可以通过以下两种方式添加新的I节点：

向文件系统添加附加的空间，扩展文件系统也向I节点表中添加了I节点。

备份数据，重建文件系统，建立更多的I节点，然后从磁带上恢复你的数据。

系统崩溃或不正确的关闭会对HFS文件系统造成灾难性的后果，且恢复过程缓慢并不可预测。

在某些情况下，可能需要重新创建文件系统并从磁带恢复数据。

**日志文件系统（JFS）：**

也被称为Veritas文件系统（vxfs）。

日志文件系统是为了克服HFS的一些不足而设计的。

这种文件系统具有快速恢复的特性。

HP的在线日志文件系统（online JFS）它基于JFS扩展，可以对文件系统进行在线管理，不用先卸载。

JFS也保存超级块的多个拷贝，与HFS不同，它能自动找到冗余超级块，所以备份不存储在sbtab文件中。

JFS的主要优点是所有对结构数据的修改都保存在日志中。

这种日志机制保证了文件系统的完整性，并且系统崩溃时能很快恢复文件系统。

如果系统崩溃，文件系统能通过应用JSF日志中的所有改变记录被迅速恢复。

系统崩溃后，简单重做日志中的事务处理，就可以在10-20秒内将文件系统结构数据恢复到相应状态。

相比于HFS，JFS另一个显著有点就是它可以动态增加I节点的数量。

与HFS一样，JFS将文件系统分成若干个JFS块，缺省每块为1KB大小。

JFS是一种以extent为基础的文件系统，为了达到性能优化，文件和目录中的数据应当是连续的。

在动态文件系统中，可能需要定期使用fsadm碎片整理工具。

内核文件不能在JFS文件系统中。

**CDFS：CD-ROM文件系统**

NFS：网络文件系统

18.4.2 硬链接和软连接

18.5 高性能文件系统

**高性能文件系统（HFS）：**

传统的HP-UX文件系统，作为/stand的文件系统。

所有HFS文件系统的前8KB空间用作HFS主超级块，包含一般的文件系统信息。

超级块还包含指向文件系统中所有其他HFS结构数据的指针。

HFS拥有多个超级块备份，位置在/var/adm/sbtab。

被损坏的HFS超级块通过这些备份进行修复。

在一个读请求中，HFS块是最小数据单元，缺省为8KB大小，有效数据块为4-64K，2的乘方。

段是用于分配的最小数据单元，HFS块可以分成多个段。

HFS便于管理，然而不能缩减它的空间，也不能方便地扩展空间，扩展前必须卸载文件系统。

当创建HFS文件系统时，必须标明你需要创建多少I节点。

I节点存放在新文件系统的I节点表中。

如果没有空闲的I节点，即使你有空闲的数据块，也不能创建新文件目录。

可以通过以下两种方式添加新的I节点：

向文件系统添加附加的空间，扩展文件系统也向I节点表中添加了I节点。

备份数据，重建文件系统，建立更多的I节点，然后从磁带上恢复你的数据。

系统崩溃或不正确的关闭会对HFS文件系统造成灾难性的后果，且恢复过程缓慢并不可预测。

在某些情况下，可能需要重新创建文件系统并从磁带恢复数据。

**18.5.1 HFS块**

在一个读请求中，HFS块是最小数据单元。可以自定义4/8/16/32/64KB.

文件小，块大：假如采用64KB块：即使数据仅512B，存储时会占据64KB空间，读取时也要读完整个64KB的块。

文件大，块小：在读取大文件时需要发出多次请求。特别是数据块不连续时，将耗费大量时间。

块的尺寸一旦在创建文件系统是被指定，他就不能改变。

**18.5.2 HFS段**

段是用于分配的最小数据单元，HFS块可以分成多个段，一个块可被分成1段，2段，4段或8段。

段的尺寸一旦在创建文件系统是被指定，他就不能改变。

一个块会包含属于不同文件的段。

18.6 日志文件系统

**日志文件系统（JFS）：**

也被称为Veritas文件系统（vxfs）。

日志文件系统是为了克服HFS的一些不足而设计的。

这种文件系统具有快速恢复的特性。

HP的在线日志文件系统（online JFS）它基于JFS扩展，可以对文件系统进行在线管理，不用先卸载。

JFS也保存超级块的多个拷贝，与HFS不同，它能自动找到冗余超级块，所以备份不存储在sbtab文件中。

JFS的主要优点是所有对结构数据的修改都保存在日志中。

这种日志机制保证了文件系统的完整性，并且系统崩溃时能很快恢复文件系统。

如果系统崩溃，文件系统能通过应用JSF日志中的所有改变记录被迅速恢复。

系统崩溃后，简单重做日志中的事务处理，就可以在10-20秒内将文件系统结构数据恢复到相应状态。

相比于HFS，JFS另一个显著有点就是它可以动态增加I节点的数量。

与HFS一样，JFS将文件系统分成若干个JFS块，缺省每块为1KB大小。

JFS是一种以extent为基础的文件系统，为了达到性能优化，文件和目录中的数据应当是连续的。

在动态文件系统中，可能需要定期使用fsadm碎片整理工具。

内核文件不能在JFS文件系统中。

18.7 创建新的文件系统

创建新的文件系统：

**18.7.1 文件系统创建过程**

要使一个文件系统真正生效，需要经过4个步骤：

**18.7.2 用newfs创建新文件系统**

newfs命令可以用于创建文件系统，如果你采用LVM，在使用newfs之前，需要先完成下面3个步骤

1）.建立物理卷，

2).利用这些物理卷创建一个或多个卷组，

3).创建逻辑卷。

执行了上面的步骤后，再用newfs在逻辑卷上创建一个文件系统，使用字符设备文件：

例：在/dev/vg03/rlvol4上创建JFS文件系统，使用下面的命令        

newfs -F vxfs /dev/vg03/rlvol4                   #在/dev/vg03/rlvol4上创建JFS文件系统

newfs -F vxfs -o largefiles /dev/vg03/rlvol5     #/dev/vg03/rlvol5上创建一个支持大文件的系统

newfs -F hfs -b 2048 /dev/vg03/rlvol5            #建一个块尺寸2KB的HFS文件系统

newfs -F vxfs -R 100 /dev/rdsk/c2t5d0 #在一个整盘方法创建的磁盘c2t5d0上建立一个JFS文件系统，并留出100MB空间用于交换：

newfs命令的一些选项：

-F                    文件系统类型。HFS或vxfs等

-s                    以块来表示文件系统尺寸，若不指定，将使用逻辑卷所有空闲空间

-o largefiles     用于支持大文件，缺省文件最大尺寸为2GB，使用后为128GB

-b                    以字节表示每个块的大小（仅用于HFS）

-i                     以字节表示每个I节点的尺寸（仅用于HFS）

-f                     以字节表示段的大小（仅用于HFS）

-R                   以MB表示文件系统尾部保留作为交换区的空间，不可以与-s一起使用

-m                   允许的剩余空间最小值，达到这个值后，则除root外其他用户不能使用FS。

*：-i 4096 表示每4KB空间需要使用1个I节点

newfs命令需要使用字符设备文件做参数，逻辑卷或磁盘会被覆盖，所以数据会被破坏。

如果没有使用-F来定义文件系统类型，将采取/etc/default下面的定义，HP11.0默认为vxfs。

（2）然后用mkdir命令为文件系统创建一个挂在用的目录

         mkdir /mnt

18.8 挂载和卸载文件系统

**18.8 挂载和卸载文件系统**

mount -F vxfs /dev/vg03/lvol4 /mnt       #把JFS文件系统/dev/vg03/lvol4挂载在/mnt目录

mount -v

bdf        #查看已挂载的文件系统。

fuser /mnt  可以查看/mnt是否正在被用户使用。

fuser -ku -c /mnt 可以把正在使用/mnt文件系统的所有进程停止下来。

       文件系统必须挂起在空目录下，如果文件系统被挂起在已经包含文件和目录的目录下，则这些文件和目录将会被隐藏。直到这个文件系统被卸载。        不可能把文件系统挂载在正在被其他用户或进程使用的目录，试图吧这个文件系统挂在已经使用的目录上会得到&quot;设备忙&quot;的信息。

umount /mnt 可以卸载挂载在/mnt目录的文件系统。

umount /dev/vg01/myfs1 卸载使用myfs1逻辑卷的文件系统。

umount -a 可以卸载所有当前挂载的文件系统。

umount -aF vxfs 可以卸载所有JFS文件系统。

mount使用的是块设备文件。

...

行信息包含了文件系统名，挂载点，文件系统类型以及其他相关选项。

**18.8.1 在启动时自动挂载**

修改/etc/fstab文件，添加一行相关信息，实现系统启动时自动挂载文件系统

/dev/vg00/lvol4 /moko xvfs delaylog 0 2

在启动过程中，脚本/sbin/init.d/localmount被执行，它调用mount -a命令，将/etc/fstab文件中所列的文件系统全部挂载。

**18.8.2 文件/etc/fstab文件示例**

/dev/vg00/lvol4   /tmp   vxfs delaylog  0  2

/dev/vg00/lvol5   /home  vxfs delaylog  0  2

/dev/vg00/lvol6   /opt   vxfs delaylog  0  2

/dev/vg00/lvol7   /usr   vxfs delaylog  0  2

/dev/vg00/lvol8   /var   vxfs delaylog  0  2

18.9 管理文件系统

**18.9.1 监视磁盘使用情况**

bdf能够显示所有已挂载的文件系统以及每个文件系统的信息：文件系统名称，总的磁盘空间，已用的磁盘空间，可用的磁盘空间，磁盘利用的百分率，挂载点。

Filesystem          kbytes    used   avail %used Mounted on

/dev/vg00/lvol3     204800   48168  155424   24% /

/dev/vg00/lvol1     295024   38856  226664   15% /stand

/dev/vg00/lvol8    4706304 1523976 3157592   33% /var

/dev/vg00/lvol7    1163264  708304  451464   61% /usr

/dev/vg00/lvol4     204800   96408  107568   47% /tmp

/dev/vg00/lvol6    1048576  766024  280360   73% /opt

/dev/vg00/lvol5    1048576    4456 1036024    0% /home

加上-i选项在输出中增加了3个文件系统可用I节点的列：

iused：文件系统上正在使用的I节点数。

ifree：文件系统上可用的i节点。

第三个位I节点的使用比例。

也可以使用du命令显示一个目录多少空间被使用。

**18.9.2 扩展卷组：**

如果在一个卷组中，没有未分配的空间，你需要先扩展卷组，可以通过增加一个硬盘来实现。通过创建一个物理卷，然后将这个新的物理卷使用vgextend命令加入到卷组中，从而增加卷组容量。

例：pvcreate /dev/rdsk/c0t3d0

      vgextend vg03 /dev/dsk/c0t3d0

**18.9.3 扩展逻辑卷：**

扩展卷组后，通过lvextend命令扩展逻辑卷的尺寸。

例：lvextend -L 800 /dev/vg03/lvol4       #将逻辑卷由本来400M增加到800M

      lvextend -L 800 /dev/vg03/lvol4 /dev/dsk/c0t3d0   #在特定磁盘上扩展逻辑卷

**18.9.4 扩展文件系统：**

扩展了逻辑卷的空间不会自动扩展文件系统的空间，应使用extendfs命令给文件系统增加空间。

在扩展之前，必须先卸载该文件系统（在线式JFS除外）。

例：extendfs -F vxfs /dev/vg03/lvo14

在线式JFS扩展系统时，不用卸载，需要使用另一个命令fsadm来扩展文件系统，例：

fsadm -F vxfs -b 819200 /mnt       #将/mnt文件系统扩展到800MB（819200KB）

18.10 文件系统修复

文件系统修复：

系统崩溃或非正常关机的关机操作都会导致文件系统元数据出现错误，这时，你应该对文件系统进行修复。

fsck命令可用来检查并修复系统。

如果系统崩溃或进行了非正常的关机操作，fsck命令会自动运行，需要时也可以手工执行。

执行fsck前，必须卸载文件系统。

如果在元数据区遇到不一致的情况，fsck命令会删除一些文件。

有些文件不能被fsck完全识别，它会被放到lost+found目录下。

在用完fsck修复完文件后，你应该从先前的备份上将一些被毁坏的文件恢复到系统上。

例：fsck -F vxfs /dev/vg03/rlvol4      

执行fsck时需要知道文件系统的类型。指定需要检查的文件系统所在磁盘或逻辑卷的字符设备文件。

fsck命令的一些选项：

-F           文件系统类型

-n           假设对fsck的所有问题回答No

-y           假设对fsck的所有问题回答yes

-b           告诉fsck去使用备用的超级块（仅适用于HFS）

-f            强制在被挂起的文件系统上执行fsck（仅适用于HFS）

-o full     强制fsck对文件系统的元数据进行全面检查而不是指重放意图日志（仅用于JFS）

-o nolog 阻止意图日志重放（仅用于JFS）

18.11重要的LVM命令

重要的LVM命令：

extendfs                扩展一个文件系统

lvchange                改变一个逻辑卷的属性

lvcreate                 创建一个逻辑卷

lvdisplay                 列出逻辑卷信息

lvextend                 扩展逻辑卷

lvlnboot                  将逻辑卷设成root ,dump 或 swap

lvreduce                 减少一个逻辑卷的尺寸

lvremove                将卷组中的一个逻辑卷删除

lvrmboot                 将逻辑卷作为root ,dump 或 swap使用

pvchange               改变一个物理卷的属性

pvcreate                 创建一个物理卷

pvdisplay                列出物理卷的属性

pvmove                   将某物理卷从一个卷组移动到另一个卷组

vgcfgbackup           备份LVM的配置信息

vgcfgrestore           从备份的LVM配置信息中恢复

vgchange                 改变一个卷组的属性

vgcreate                   创建一个卷组

vgdisplay                  列出一个卷组的属性

vgextend                   扩展卷组

vgexport                    从系统输出一个卷组

vgimport                    从系统输入一个卷组

vgreduce                   通过删除物理卷来减小卷组

vgremove                  删除一个卷组

第19章 用户和组管理

19.1 管理用户

19.1 管理用户

用户名：

用户ID：

用户口令：6-8个字符

**19.1.1 生成用户**

#useradd -m username # -m 生成/home/username目录，并拷贝/etc/skel目录下文件

#useradd -D # 显示缺省设置

**19.1.2 删除用户**

#userdel    username # 只删除/etc/passwd 中的Item

#userdel -r username # -r 删除主目录

**19.1.3 编辑用户**

#usermod

**19.1.4 用户失效和过期**

#useradd/usermod -f positive-integer        #设置inactive过期时间

#useradd/usermod -e                                #设置过期日期

#usermod

**-f inactive**    Specifies the maximum number of days of continuous inactivity of the login before the login is declared invalid.  Normal values are positive integers, while a value of -1 defeats this status.

**-e expire**      Specifies the date on which this login can no longer be used.  After expire, no user will be able to access this login.  This option is used to create temporary logins.  expire, which is a date,may be typed in any format, except a Julian date.For example, a date may be entered in either of the following formats:

       July 13, 1993

       7/13/93

19.2 管理组

19.2

/etc/group

**19.2.1**

19.2.2 生成，删除，编辑

#groupadd

#groupdel

#groupmod

19.2.3 多个组成员关系

#id grouop_name

#groups group_name

#newgrp group_name #临时使用new_group组，作为新的当前用户组

19.3 口令文件

19.4 组文件

19.4

/etc/group

**19.4.1 限制用户古访问**

**19.4.2 确认口令和组文件的一致性**

pwck        主要检查/etc/passwd与/etc/group的一致性

grpck        主要检查/etc/group与/etc/passwd的一致性

#vipw 用来编辑/etc/passwd文件. 该命令运行时会在/etc/passwd上加锁，防止其他用户修改自己口令引起的不一致。

19.5 纲要目录

/etc/skel

第20章 处理HP-UX进程

20.1 进程表

进程表是一个内核数据结构

PID        进程ID        

PPID        父进程

STAT        当前进程状态

UID        创建进程的用户

GID        属组的组ID

C/CPU        处理器利用率

PRI        进程优先级

NI        用在优先级计算中的nice值

ADDR        进程的内存地址

SZ        进程映象的物理分页大小

WCHAN        进程等待的事件

STIME        进程的启动时间

TTY        进程的控制终端

TIME        进程的累积执行时间

COMM        启动进程的命令

MAX        允许打开的最大文件数

       在系统启动时，交换进程（PID：0）被创建。交换进程初始化init进程（PID：1）。init进程调用fork创建其他进程。

20.2 进程状态

          state          The state of the process:

                              0    Nonexistent

                              S    Sleeping

                              W    Waiting

                              R    Running

                              I    Intermediate

                              Z    Terminated

                              T    Stopped

                              X    Growing

20.3 列出进程

进程表中的域

20.4 给进程发送信号

信号用于给一个进程发送一些信息或处理一个例外事件。信号可以由killm命令发送给进程。

# kill -l

1) HUP                                        23) WINCH

2) INT                                        24) STOP

3) QUIT                                       25) TSTP

4) ILL                                        26) CONT

5) TRAP                                       27) TTIN

6) ABRT                                       28) TTOU

7) EMT                                        29) URG

8) FPE                                        30) LOST

9) KILL                                       31) RESERVED

10) BUS                                        32) DIL

11) SEGV                                       33) XCPU

12) SYS                                        34) XFSZ

13) PIPE                                       35) The specified trap syntax is not correct.

14) ALRM                                       36) The specified trap syntax is not correct.

15) TERM                                       37) RTMIN

16) USR1                                       38) RTMIN+1

17) USR2                                       39) RTMIN+2

18) CHLD                                       40) RTMIN+3

19) PWR                                        41) RTMAX-3

20) VTALRM                                     42) RTMAX-2

21) PROF                                       43) RTMAX-1

22) IO                                         44) RTMAX

20.5 进程的nice值

**20.5进程nice值**

进程nice值优先级从0-39。

子进程继承父进程的nice值。

init进程nice值为20（系统进程的默认nice值），所以系统中大多数进程都继承20这个nice值。

nice命令用来改变新经常的nice值。

renice命令用来改变正在运行的进程的nice值。

**20.5.1 列出nice值**

# ps -efl

#nice  -5 command        #以nice值25运行该命令

#nice --5 command        #以nice值15运行该命令

参数为与系统默认nice值的差值

# commdan &amp;                #以&amp;运行的命令，缺省nice值等价于nice -4(即nice值为24）。

# nice -5 command &amp;        #程序的nice值与缺省nice的差5，即nice值为29.

**20.5.2 改变正在运行的进程的nice值**

_#renice -n newoffset PID/-u UID/-g GID_

-n newoffset   Change the system nice value of each affected

                         process to 20 + newoffset.  If the UNIX95

                         environment variable is set, the  system nice

                         value of each affected process is changed to

                         current nice value + newoffset.

                         If newoffset is negative, the system nice value is

                         set to 20 minus the absolute value of newoffset.

                         If the UNIX95 environment variable is set and the

                         newoffset is negative, the system nice value is

                         set to current nice value minus the absolute value

                         of newoffset.  Only users with appropriate

                         privileges can reduce the system nice value or set

                         it to less than 20\.  If this option is omitted,

                         newoffset defaults to 10.

-u        改变所有属于该用户的进程的nice值

-g        改变所有属于该组的进程nice值

20.6 一些有用的命令

**timex**

timex reports in seconds the elapsed time, user time, and system time

     spent in execution of the given command.

Example:

#timex ll /etc

......

real        0.17 #进程的执行时间

user        0.02 #用户模式下生成该进程使用的时间

sys         0.03 #系统迷失下生成该进程使用的时间

**trap**

trap命令捕捉信号，如果一个特定的信号被接收就执行一个动作

#trap -- &amp;apos;echo &amp;apos;\&amp;apos;&amp;apos;logout&amp;apos;\ EXIT        #输入exit是执行 echo logoout

#trap -- &amp;apos;ls /etc&amp;apos; INT                #通过CTRL+C发送INT信号，ls /etc 命令将被执行

#trap -- pwd DEBUG

#trap -- date DEBUG

#trap -- &quot;&quot; DEBUG

#trap        #不带参数，列出当前陷阱。

第21章 在HP-UX中打印

第22章 内存和交换分区管理

22.1 系统内存和交换空间

22.2 交换空间的类型

22.3 创建交换空间

22.4 监视交换空间

# swapinfo

PCT USED：已用交换空间的百分率。

START/LIMIT ：一般为0,强加于交换空间的限制。

KB RESERVE：文件系统上预留的二进制文件的空间总量。

PRI：显示交换分区的优先级。

swapinfo option：

-d        只显示设备交换区

-f        只显示文件系统交换区

-m        一MB代替KB

pt        在输出的结尾添加一个总计行，显示物理内存和交换区的总量

22.5 交换空间的优先级和性能

第23章 系统备份和恢复

23.1备份类型

23.1备份类型

23.1 备份类型

23.2备份和恢复的方法

23.2

tar                        #最广泛

fbackup/frecover        #HP-UX专用

cpio                        #

dump/restore

vxdump/vxrestore

pax

dd                        #裸数据拷贝

23.3使用fbackup/frecover

**23.3 使用fbackup/frecover**

23.3.1 创建备份

#fbackup -v -f /dev/rmt/0m -i /etc        #把/etc下面的数据备份到/dev/rmt/0m；

                                               # -i 指定要备份的目录文件；-e 用来排除一些目录；

                                                #

#fbackup -v -f /dev/rmt/0m -i /etc -e /etc/lp        #把/etc下面的数据备份到/dev/rmt/0m，但不包含/etc/lp文件

**23.3.2 使用图文件**

Example：

# fbackup -v -g gfile -f /dev/rmt/0m

i        表示包含该目录

e        表示不包含该目录

**23.3.3 创建增量备份**

fbackup -u option:更新备份记录文件/var/adm/fbackupfiles/dates.

该文件格式：

1.  日期、开始时间和备份的结束时间。
2.  备份级别
3.  用于fbackup命令的图文件

fbackup options:

-f        #用作备份介质设备

-0到-9        #备份级别

-u        #更新/var/adm/fbackupfiles/dates文件

-v        #详细模式：显示命令的动作

-i        #在备份中包括的路径

-e        #在备份中排除的路径

-g        #用于fbackup的图文件

-I        #生成一个显示备份的文件列表的索引文件

**23.3.4 恢复备份数据**

frecover options:

-r        #恢复所有内容

-g        #为选择恢复的文件使用图文件

-v        #详细模式；显示命令的动作

-o        #强制命令用一个旧文件覆盖一个新文件

-x        #恢复用图文件声明的文件或用-i和-e选项选择的文件

-i        #在恢复过程中包含的文件

-e        #在恢复过程中排除的文件

-f        #使用那个设备恢复数据

23.4使用tar

23.4

23.4.1 用tar创建备份

# tar -cvf /dev/rmt/0m /etc/ home #备份/etc,/home到默认的磁带设备/dev/rmt/0m

# tar -cvf /extra/home.tar        /home        #备份/home到文件home.tar

# tar -tvf /dev/rmt/0m                #流出备份内容

# tar -tv                                # -f  /dev/rmt/0m是缺省选项，可以省略

23.4.2 使用tar恢复数据

# tar -xvf /dev/rmt/0m

23.5使用SAM

23.6使用Ignite-UX

**23.6**

Ignit-UX 创建一个可用于引导的磁带，重建一个可引导的最小系统。

恢复磁带必须包含：

1.  系统引导盘引导区
2.  根卷组（vg00）
3.  重要系统文件的映象

**23.6.1 创建恢复磁带**

/opt/ignite/bin/make_recovery 帮助创建恢复磁带

缺省时以下4个目录被备份：

1.  /stand #包含HP-UX内核
2.  /sbin        #包含引导时使用的命令和脚本
3.  /dev        #包含那些用于跟卷组的设备文件的/dev目录
4.  /etc        #包含配置信息

Example：

# /opt/ignite/bin/make_recovery -A -C -v -d /dev/rmt/0m

# /opt/ignite/bin/make_recovery -A -C -v        # -d /dev/rmt/0m 省却缺省选项

# /opt/ignite/bin/make_recovery -ACv

-A #备份vg00上所有数据

-C #创建备份日志文件,用来更新一个可恢复的磁带 /var/opt/ignite/recovery/makerec.last

23.6.2 更新恢复磁带

# /opt/ignite/bin/check_recovery #这个命令比较文件系统和Ignit-UX的日志信息，用来检查是否需要更新Ignite-UX恢复磁带。

第24章 自动化作业

24.1介绍cron

**24.**

/var/spool/cron/atjobs        # at job 存放位置

/var/spool/cron/atjobs/root        # cron job 存放位置

**24.1.1 cron进程**

cron进程在runleve 1 停止，

cron进程在runleve 2 启动。

/etc/rc.config.d/cron文件中的变量CRON控制启动与否：

CRON=0        进程不启动

CRON=1        进程启动

/sbin/init.d/cron start        #启动脚本link到/sbin/rc2.d/S730cron

/sbin/init.d/cron stop        #停止脚本link到/sbin/rc1.d/K270cron

**24.1.2 运行用户访问**

/var/adm/cron/cron.allow        #允许访问cron进程的用户列表

/var/adm/cron/cron.deny        #拒接访问cron进程的用户列表

cron.allow/deny aaply policy:

24.1.3 日志文件

/var/adm/cron/log

24.2使用cron

**24.2**

24.2.1 crontab文件格式

分钟        小时        日期        月份        星期        命令

**24.2.2 编辑crontab**

crontab -e #编辑用户crontab

crontab -l #列出用户crontab

crontab -r #删除用户crontab

24.2使用at

24.3

**24.3.1 发出一个作业**

**24.3.2 列出和删除一个作业**

root@cschp87 # at now + 1 hours                #生成一个作业

ls -l

warning: commands will be executed using /usr/bin/sh

job 1394012472.a at Wed Mar  5 04:41:12 2014

root@cschp87 # at -l                                #列出作业

user = root     1394012472.a    Wed Mar  5 04:41:12 2014

root@cschp87 # at -r 1394012472.a                #删除作业

root@cschp87 # at -l                        #列出作业

#more /var/spool/cron/atjobs/1394012681.a #作业被保存的位置

: at job

export _; _=/usr/bin/at

export MANPATH; MANPATH=/usr/share/man/%L:/usr/share/man:/usr/contrib/man/%L:/usr/contrib/man:/usr

/local/man/%L:/usr/local/man:/opt/upgrade/share/man/%L:/opt/upgrade/share/man:/usr/dt/share/man:/o

pt/pd/share/man/%L:/opt/pd/share/man:/opt/hparray/share/man/%L:/opt/hparray/share/man:/opt/ignite/

share/man/%L:/opt/ignite/share/man:/opt/perf/man/%L:/opt/perf/man:/opt/OV/man/itose/%L:/opt/OV/man

/itose:/opt/prm/man:/opt/resmon/share/man:/opt/omni/lib/man:/opt/hpnp//man:/opt/pred/share/man/%L:

/opt/pred/share/man:/opt/graphics/common/man

export SSH_TTY; SSH_TTY=/dev/pts/0

export PATH; PATH=/usr/sbin:/usr/bin:/usr/ccs/bin:/usr/contrib/bin:/opt/nettladm/bin:/opt/fc/bin:/

opt/fcms/bin:/opt/upgrade/bin:/opt/pd/bin:/usr/bin/X11:/usr/contrib/bin/X11:/opt/hparray/bin:/opt/

perf/bin:/opt/OV/bin/OpC:/opt/prm/bin:/opt/resmon/bin:/opt/ignite/bin:/opt/omni/bin:/opt/hpnp//bin

:/opt/pred/bin:/opt/graphics/common/bin:/usr/sbin/diag/contrib:/opt/fortran90/bin:/opt/fortran90:/

EngLib/Thermopp/bin:/opt/fortran/bin:/opt/fortran:/opt/cobol/bin:/sbin:/home/root:/opt/perf/bin:/u

sr/contrib/bin

export COLUMNS; COLUMNS=98

export EDITOR; EDITOR=vi

export HISTFILE; HISTFILE=/root/.sh_history

export LOGNAME; LOGNAME=root

export MAIL; MAIL=/var/mail/root

export ERASE; ERASE=\^H

export USER; USER=root

export DISPLAY; DISPLAY=143.219.221.127:10.0

export SHELL; SHELL=/sbin/sh

export HISTSIZE; HISTSIZE=1000

export HOME; HOME=/root

export ArrayID; ArrayID=ALTHP87_AR01

export SSH_CONNECTION; SSH_CONNECTION=10.246.2.105\ 64639\ 143.219.221.127\ 22

export SSH_CLIENT; SSH_CLIENT=10.246.2.105\ 64639\ 22

export TERM; TERM=xterm

export PWD; PWD=/sbin/rc2.d

export TZ; TZ=EST5EDT

export ENV; ENV=/root/.kshrc

export LINES; LINES=32

# @(#) Revision: 27.1

cd /sbin/rc2.d

ulimit unlimited

umask 22

ls -l /                #要执行的command.

**24.3.3 access/deny控制**

/var/adm/cron/at.allow

/var/adm/cron/at.deny

第25章 系统性能监视

25.1系统性能监视工具

25.1

1.  iostat
2.  vmstat
3.  netstat
4.  top
5.  sar
6.  ClancePlus

**25.1.1 监视内存性能**

# vmstat -n

VM

      memory                     page                          faults

    avm    free   re   at    pi   po    fr   de    sr     in     sy    cs

   8660  1202711   5    1     0    0     2    0     0    1078    778   120

CPU

   cpu          procs

us sy id    r     b     w

 1  0 99    0     0     0

 1  0 99

 0  0 99

 1  0 99

**25.1.2 监视磁盘性能**

**25.1.3 使用top**

# top

System: cschp87                                       Wed Mar  5 04:45:39 2014

Load averages: 0.01, 0.01, 0.01

112 processes: 109 sleeping, 3 running

Cpu states:

CPU   LOAD   USER   NICE    SYS   IDLE  BLOCK  SWAIT   INTR   SSYS

0    0.00   0.0%   0.0%   0.4%  99.6%   0.0%   0.0%   0.0%   0.0%

1    0.00   0.0%   0.0%   0.0% 100.0%   0.0%   0.0%   0.0%   0.0%

2    0.03   0.2%   0.0%   0.2%  99.6%   0.0%   0.0%   0.0%   0.0%

3    0.00   0.0%   0.0%   0.2%  99.8%   0.0%   0.0%   0.0%   0.0%

---   ----  -----  -----  -----  -----  -----  -----  -----  -----

avg   0.01   0.0%   0.0%   0.2%  99.8%   0.0%   0.0%   0.0%   0.0%

Memory: 67764K (34248K) real, 58140K (33236K) virtual, 4813648K free  Page# 1/7

CPU TTY    PID USERNAME PRI NI   SIZE    RES STATE    TIME %WCPU  %CPU COMMAND

3   ?      36 root     152 20  1856K     0K run   1721:50  1.17  1.17 vxfsd

2   ?     430 root     154 20  1732K   248K sleep 4598:06  0.19  0.19 syncer

3 pts/0  4820 root     178 20  2696K   460K run      0:00  0.24  0.17 top

0   ?    1355 root     127 20 23000K  4284K sleep 1429:04  0.17  0.17 scopeux

2   ?    1603 root     154 20 11096K  1464K sleep 4048:32  0.16  0.16 ARMServer

0   ?       2 root     128 20    32K     0K sleep  684:02  0.15  0.15 vhand

1   ?    1319 root     -16 20 21888K  8864K run   2051:36  0.07  0.07 midaemon

0   ?    1532 root     168 20  2848K   336K sleep  132:04  0.05  0.05 p_client

0   ?    1654 root     154 10  4808K  1332K sleep 1111:20  0.05  0.05 psmctd

1   ?    2369 root     154 20 13920K  1968K sleep  853:43  0.05  0.05 alarmgen

0   ?   27013 root     154 20  7316K   572K sleep    0:10  0.05  0.04 sshd:

3   ?       3 root     128 20    32K     0K sleep 1443:27  0.04  0.04 statdaemon

1   ?    1651 root     158 10  2376K   260K sleep  520:23  0.03  0.03 cclogd

3   ?     571 root     127 20  3484K   456K sleep  199:20  0.03  0.03 netfmt

3   ?       0 root     128 20    32K     0K sleep   10:21  0.02  0.02 swapper

0   ?       1 root     168 20   496K   220K sleep   31:56  0.02  0.02 init

1   ?       4 root     128 20    32K     0K sleep   35:36  0.02  0.02 unhashdaemon

1.  每5秒显示一屏幕信息
2.  最顶行显示系统名称和收集时间

CPU部分：

1.  系统负载：当前，5分钟前，15分钟前的负载状况
2.  当前系统中的进程数量和状态（sleeping/running）

内存区：

1.  已安装的物理内存总量
2.  活动的物理内存
3.  虚拟内存
4.  可用虚拟内存
5.  可以内存总计

进程区：

**25.1.4 使用系统行为报告**

# sar -o /home/root/sar.dat 10 360        #使用sar监控系统1小时（10×360S=3600S=1HOUR），并生成日志文件sar.data

# sar -f /home/root/sar.dat                #读取监控日志文件

# sar -u 1 5 #用sar监视CPU,每秒一次共5次

# sar -b 1 5 #用sar命令监视缓存区寄存器，每秒一次共5次

第3篇 HP-UX网络管理

第26章 基本网络概念

第27章 网络部件和拓扑

第28章 TCP/IP

第29章配置LAN适配器

29.1 配置LAN适配器

**29.1 配置LAN适配器**

# lsdev -C lan #列出LAN适配器配置的驱动程序

   Character     Block       Driver          Class

      14          -1         btlan           lan

      15          -1         maclan          lan

      45          -1         fcT1_cntl       lan

      50          -1         fddi4           lan

      75          -1         btlan6          lan

      79          -1         fcgsc_lan       lan

     114          -1         btlan3          lan

     191          -1         fddi            lan

**29.1.1 LAN适配器命令规则**

**29.1.2 检测LAN适配器**

# ioscan -funC lan #用于检测LAN适配器（1）

Class     I  H/W Path     Driver    S/W State   H/W Type     Description

=========================================================================

lan       0  0/0/0/0      btlan3    CLAIMED     INTERFACE    HP PCI 10/100Base-TX Core                /dev/diag/lan0  /dev/ether0

lan       7  0/4/0/0.5    fcT1_cntl CLAIMED     INTERFACE    HP Fibre Channel Mass Storage Cntl        /dev/fcms7

lan       1  0/8/0/0      fddi4     CLAIMED     INTERFACE    PCI FDDI Adapter HP A3739A

lan       2  1/2/0/0      fddi4     CLAIMED     INTERFACE    PCI FDDI Adapter HP A3739A

lan       3  1/8/0/0/4/0  btlan     CLAIMED     INTERFACE    HP A5506A PCI 10/100Base-TX 4 port        /dev/diag/lan3  /dev/ether3     /dev/lan3

lan       4  1/8/0/0/5/0  btlan     CLAIMED     INTERFACE    HP A5506A PCI 10/100Base-TX 4 port        /dev/diag/lan4  /dev/ether4     /dev/lan4

lan       5  1/8/0/0/6/0  btlan     CLAIMED     INTERFACE    HP A5506A PCI 10/100Base-TX 4 port        /dev/diag/lan5  /dev/ether5     /dev/lan5

lan       6  1/8/0/0/7/0  btlan     CLAIMED     INTERFACE    HP A5506A PCI 10/100Base-TX 4 port        /dev/diag/lan6  /dev/ether6     /dev/lan6

lan       8  1/12/0/0.5   fcT1_cntl CLAIMED     INTERFACE    HP Fibre Channel Mass Storage Cntl        /dev/fcms8

S/W State：CLAIMED        表示软件驱动程序已经成功的绑定到适配器上。

H/W Type：INTERFACE  表示硬件类型是一个接口适配器。

# lanscan #用于检测LAN适配器（2）

Hardware        Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path            Address        In# State NamePPA        ID  Type      Support Mjr#

0/0/0/0          0x001083274748 0   UP    lan0 snap0     1   ETHER     Yes     119

1/8/0/0/4/0        0x0010831878BF 3   UP    lan3 snap3     2   ETHER     Yes     119

1/8/0/0/5/0        0x001083187870 4   UP    lan4 snap4     3   ETHER     Yes     119

1/8/0/0/6/0        0x00108318883A 5   UP    lan5 snap5     4   ETHER     Yes     119

1/8/0/0/7/0        0x001083187897 6   UP    lan6 snap6     5   ETHER     Yes     119

1/2/0/0          0x0060B0581736 2   DOWN  lan2           6   FDDI      Yes     119

0/8/0/0          0x0060B05816A3 1   DOWN  lan1           7   FDDI      Yes     119

# lanscan -v # -v option显示扩展的站地址（Extended Station Address）和支持的封装方式（LLC Encapsulation Methods）

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

0/0/0/0  0x001083274748 0   UP    lan0 snap0     1   ETHER     Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x001083274748                             IEEE HPEXTIEEE SNAP ETHER NOVELL

Driver Specific Information

btlan3

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

1/8/0/0/4/0 0x0010831878BF 3   UP    lan3 snap3     2   ETHER     Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x0010831878BF                             IEEE HPEXTIEEE SNAP ETHER NOVELL

Driver Specific Information

btlan

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

1/8/0/0/5/0 0x001083187870 4   UP    lan4 snap4     3   ETHER     Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x001083187870                             IEEE HPEXTIEEE SNAP ETHER NOVELL

Driver Specific Information

btlan

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

1/8/0/0/6/0 0x00108318883A 5   UP    lan5 snap5     4   ETHER     Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x00108318883A                             IEEE HPEXTIEEE SNAP ETHER NOVELL

Driver Specific Information

btlan

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

1/8/0/0/7/0 0x001083187897 6   UP    lan6 snap6     5   ETHER     Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x001083187897                             IEEE HPEXTIEEE SNAP ETHER NOVELL

Driver Specific Information

btlan

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

1/2/0/0  0x0060B0581736 2   DOWN  lan2           6   FDDI      Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x0060B0581736                             IEEE HPEXTIEEE SNAP

Driver Specific Information

fddi4

-------------------------------------------------------------------------------

Hardware Station        Crd Hdw   Net-Interface  NM  MAC       HP-DLPI DLPI

Path     Address        In# State NamePPA        ID  Type      Support Mjr#

0/8/0/0  0x0060B05816A3 1   DOWN  lan1           7   FDDI      Yes     119

Extended Station                           LLC Encapsulation

Address                                    Methods

0x0060B05816A3                             IEEE HPEXTIEEE SNAP

Driver Specific Information

fddi4

-------------------------------------------------------------------------------

29.3 添加路由

**29.3 添加路由**

ROUTE_GATEWAY[1]=&quot;143.219.220.2&quot;

ROUTE_DESTINATION[1]=&quot;default&quot;

ROUTE_COUNT[1]=&quot;1&quot;

# netstat -rn

Routing tables

Dest/Netmask          Gateway            Flags  Refs       Use  Interface  Pmtu

127.0.0.1             127.0.0.1          UH       0   11834832  lo0        4136

10.0.0.87             10.0.0.87          UH       0          0  lan5       4136

143.219.221.127       143.219.221.127    UH       0   36186403  lan0       4136

143.219.220.0         143.219.221.127    U        2          0  lan0       1500

default               143.219.220.2      UG       0          0  lan0       1500

**29.3.1 创建一个路由**

# route add net   192.168.4.0 netmask 255.255.255.0 192.168.2.1  # 添加到网络 192.168.4.0 /24 的路由

# route add host 192.168.5.3 netmask 255.255.255.0 192.168.2.1        # 添加到主机 192.168.5.3 /24 的路由

#route -f # 刷新路由表

**29.3.2 删除一个路由**

# route del net   192.168.4.0 netmask 255.255.255.0 192.168.2.1

# route del host 192.168.5.3 netmask 255.255.255.0 192.168.2.1

29.3.3 缺省路由

# route add default 192.168.2.1 1

29.2 给LAN适配器配置一个IP地址

**29.2 给LAN适配器配置一个IP地址**

# ifconfig lan0        #查看配置信息

# netatat -in                #查看配置信息

# ifconfig lan1 192.168.3.1 netmask 255.255.255.0 brodcast 192.168.3.255 up #配置IP地址

**29.2.1 使用/etc/rc.config.d/netconf文件在启动时启动LAN适配器**

/sbin/ini.d/net 脚本调用/etc/rc.config.d/netconf 初始化网络配置信息

**Examle:**

# cat /etc/rc.config.d/netconf |grep -v &quot;#&quot;

HOSTNAME=&quot;cschp87&quot;

OPERATING_SYSTEM=HP-UX

LOOPBACK_ADDRESS=127.0.0.1

INTERFACE_NAME[0]=&quot;lan0&quot;

IP_ADDRESS[0]=&quot;143.219.221.127&quot;

SUBNET_MASK[0]=&quot;255.255.252.0&quot;

BROADCAST_ADDRESS[0]=&quot;&quot;

INTERFACE_STATE[0]=&quot;up&quot;

DHCP_ENABLE[0]=0

INTERFACE_NAME[1]=&quot;lan5&quot;

IP_ADDRESS[1]=&quot;10.0.0.87&quot;

SUBNET_MASK[1]=&quot;255.0.0.0&quot;

BROADCAST_ADDRESS[1]=&quot;&quot;

INTERFACE_STATE[1]=&quot;up&quot;

DHCP_ENABLE[1]=0

GATED=0

GATED_ARGS=&quot;&quot;

RDPD=0

RARP=0

ROUTE_GATEWAY[1]=&quot;143.219.220.2&quot;

ROUTE_DESTINATION[1]=&quot;default&quot;

ROUTE_COUNT[1]=&quot;1&quot;

**29.2.2 为一个LAN指定多个IP地址**

# ifconfig lan1:1 192.168.3.2 netmask 255.255.255.0 brodcast 192.168.3.255 up

# netstat -ni #查看配置信息

**29.2.3 更新/etc/hosts文件**

# The form for each entry is:

# &lt;internet address&gt;    &lt;official hostname&gt; &lt;aliases&gt;

29.5 LAN Stroube Shooting

29.5 LAN Stroube Shooting

物理 issues:

1.  网络适配器没有正确安装。
2.  线缆没有连接好。
3.  LAN 网络问题。
4.  路由器问题。

配置 issues:

1.  IP 地址配置不当 / 错误。
2.  掩码配置不当 / 错误。
3.  路由配置不当 / 错误。

TS tools:

#ping

#lanscan        # 列出 LAN 适配器

#netstat -in        # 列出 IP 地址

#netstat -rn        # 列出路由信息

**29.5.1 netstat**

#netstat -sv        # 每一协议的网络行为统计信息

tcp:

       4268394282 packets sent

               4120271990 data packets (412936107 bytes)

               19535104 data packets (1742222447 bytes) retransmitted

               147902248 ack-only packets (9878881 delayed)

               10 URG only packets

               75 window probe packets

               54214 window update packets

               20438836 control packets

       2373900604 packets received

               1941654464 acks (for 422894216 bytes)

               151098335 duplicate acks

               0 acks for unsent data

               343825794 packets (2277887989 bytes) received in-sequence

               793 completely duplicate packets (1133666 bytes)

               8714 packets with some dup, data (10540237 bytes duped)

               1488631 out of order packets (2122738316 bytes)

               0 packets (0 bytes) of data after window

               80 window probes

               275969166 window update packets

               1196 packets received after close

               0 segments discarded for bad checksum

               0 bad TCP segments dropped due to state change

       2232693 connection requests

       2111848 connection accepts

       4344541 connections established (including accepts)

       4382994 connections closed (including 38478 drops)

       11926 embryonic connections dropped

       1906656991 segments updated rtt (of 1906656991 attempts)

       863159 retransmit timeouts

               9727 connections dropped by rexmit timeout

       75 persist timeouts

       11791948 keepalive timeouts

               11754422 keepalive probes sent

               22 connections dropped by keepalive

       184 connect requests dropped due to full queue

       2184 connect requests dropped due to no listener

udp:

       0 incomplete headers

       0 bad checksums

       0 socket overflows

ip:

       2794923783 total packets received

       0 bad IP headers

       4044824 fragments received

       0 fragments dropped (dup or out of space)

       56 fragments dropped after timeout

       0 packets forwarded

       0 packets not forwardable

icmp:

       1225638 calls to generate an ICMP error message

       0 ICMP messages dropped

       Output histogram:

        echo reply: 1223398

        destination unreachable: 2184

        source quench: 0

        routing redirect: 0

        echo: 0

        time exceeded: 56

        parameter problem: 0

        time stamp: 0

        time stamp reply: 0

        address mask request: 0

        address mask reply: 0

       0 bad ICMP messages

       Input histogram:

        echo reply: 720910

        destination unreachable: 1618

        source quench: 0

        routing redirect: 8990

        echo: 1223398

        time exceeded: 152643

        parameter problem: 0

        time stamp request: 0

        time stamp reply: 0

        address mask request: 0

        address mask reply: 0

       1223398 responses sent

igmp:

       1432699 messages received

       0 messages received with too few bytes

       0 messages received with bad checksum

       1432699 membership queries received

       0 membership queries received with incorrect fields(s)

       0 membership reports received

       0 membership reports received with incorrect field(s)

       0 membership reports received for groups to which this host belongs

       0 membership reports sent

# lanadmin 直接或交互的进行一下操作：

1.  显示和改变站的物理地址。
2.  显示和改变最大传输单元 MUT 。
3.  显示和改变速率设置（部分适配器不适应）。
4.  显示和清空 LAN 适配器和统计数据。
5.  重置网络接口。

**29.5.2 lanadmin**

# lanadmin -a 2                # 显示 lan2 的适配器物理地址

Station Address                 = 0x0060b0581736

# lanadmin -s 2                # 显示 lan2 的的速率

Speed                           = 100000000

# lanadmin -m 2                # 显示 lan2 的适配器 MTU

MTU Size                        = 4352

# lanadmin -M 1500 2        # 改变 lan2 的适配器 MTU

#lanadmin                # 交互式

**29.5.3 ndd 调整** **TCP/IP** **参数**

# ndd -h supported   #查看支持的修改的参数

SUPPORTED ndd tunable parameters on HP-UX:

IP:

   ip_def_ttl            -  Controls the default TTL in the IP header

   ip_enable_udp_bcastrecv  - Controls receiving of broadcast packets by UDP sockets

   ip_forward_directed_broadcasts -  Controls subnet broadcasts packets

   ip_forward_src_routed -  Controls forwarding of source routed packets

   ip_forwarding         -  Controls how IP hosts forward packets

   ip_fragment_timeout   -  Controls how long IP fragments are kept

   ip_ire_gw_probe            - Enable dead gateway probes

   ip_icmp_return_data_bytes  -  Maximum number of data bytes in ICMP

   ip_ill_status         -  Displays a report of all physical interfaces

   ip_ipif_status        -  Displays a report of all logical interfaces

   ip_ire_hash           -  Displays all routing table entries, in the order

                              searched when resolving an address

   ip_ire_status         -  Displays all routing table entries

   ip_ire_cleanup_interval  - Timeout interval for purging routing entries

   ip_ire_flush_interval    - Routing entries deleted after this interval

   ip_ire_gw_probe_interval - Probe interval for Dead Gateway Detection

   ip_ire_pathmtu_interval  - Controls the probe interval for PMTU

   ip_ire_redirect_interval - Controls &amp;apos;Redirect&amp;apos; routing table entries

   ip_max_bcast_ttl      -  Controls the TTL for broadcast packets

   ip_pmtu_strategy      -  Controls the Path MTU Discovery strategy

   ip_reass_mem_limit    -  Maximum number of bytes for IP reassembly

   ip_send_redirects     -  Sends ICMP &amp;apos;Redirect&amp;apos; packets

   ip_send_source_quench -  Sends ICMP &amp;apos;Source Quench&amp;apos; packets

   ip_strong_es_model    -  Controls support for &amp;apos;Strong End-System Model&amp;apos;

   ip_udp_status         -  Reports IP level UDP fanout table

TCP:

   tcp_conn_request_max     -  Max number of outstanding connection request

   tcp_cwnd_initial         -  Initial size of the congestion window as a

                                 multiple of the MSS.

   tcp_deferred_ack_max     -  Upper limit on the number of bytes of data that

                                 can be received without an ACK.

   tcp_do_conn_options      -  Copy IP options into T_CONN_IND messages

   tcp_fin_wait_2_timeout   -  Length of time a TCP connection spends in

                                 FIN_WAIT_2

   tcp_ignore_path_mtu      -  Disable setting MSS from ICMP &amp;apos;Frag Needed&amp;apos;

   tcp_ip_abort_cinterval   -  R2 during connection establishment

   tcp_ip_abort_interval    -  R2 for established connection

   tcp_ip_notify_cinterval  -  R1 during connection establishment

   tcp_ip_notify_interval   -  R1 for established connection

   tcp_ip_ttl               -  TTL value inserted into IP header

   tcp_keepalive_detached_interval - Send keepalive probes for detached TCP

   tcp_keepalive_interval   -  Interval for sending keepalive probes

   tcp_largest_anon_port    -  Largest anonymous port number to use

   tcp_recv_hiwater_def     -  Maximum receive window size

   tcp_recv_hiwater_lfp     -  Maximum receive window size for fast links

   tcp_recv_hiwater_lnp     -  Maximum receive window size for slow links

   tcp_rexmit_interval_initial - Initial value for round trip time-out

   tcp_rexmit_interval_initial_lnp - tcp_rexmit_interval_initial for LNP

   tcp_rexmit_interval_max  -  Upper limit for computed round trip timeout

   tcp_rexmit_interval_min  -  Lower limit for computed round trip timeout

   tcp_sack_enable          -  Enable TCP Selective Acknowledgement (RFC 2018)

   tcp_smoothed_rtt         -  An alternate method for computing round trip

                                 time

   tcp_sth_rcv_hiwat        -  Sets the flow control high water mark

   tcp_sth_rcv_lowat        -  Sets the flow control low water mark

   tcp_syn_rcvd_max         -  Controls the SYN attack defense of TCP

   tcp_status               -  Get netstat-like TCP instances information

   tcp_time_wait_interval   -  How long stream persists in TIME_WAIT

   tcp_ts_enable            -  Enable TCP timestamp option

   tcp_tw_cleanup_interval  -  TIME_WAIT timeout expiration checking interval

   tcp_xmit_hiwater_def     -  The amount of unsent data that triggers

                                 TCP flow control

   tcp_xmit_hiwater_lfp     -  The amount of unsent data that triggers

                                 TCP flow control for fast links

   tcp_xmit_hiwater_lnp     -  The amount of unsent data that triggers

                                 TCP flow control for slow links

   tcp_xmit_lowater_def     -  The amount of unsent data that relieves

                                 TCP flow control

   tcp_xmit_lowater_lfp     -  The amount of unsent data that relieves

                                 TCP flow control for fast links

   tcp_xmit_lowater_lnp     -  The amount of unsent data that relieves

                                 TCP flow control for slow links

UDP:

   udp_def_ttl              -  Default TTL inserted into IP header

   udp_largest_anon_port    -  Largest anonymous port number to use

   udp_recv_hiwater_max     -  Upper bound on UDP receive buffer size

   udp_status               -  Get UDP instances information.

RAWIP:

   rawip_def_ttl            -  Default TTL inserted into IP header

   rawip_recv_hiwater_max   -  The maximum size of the RAWIP receive buffer

ARP:

   arp_cache_report         -  Displays the ARP cache

   arp_cleanup_interval     -  Controls how long ARP entries stay in the

                                 ARP cache

   arp_defend_interval      -  Seconds to wait before initially defending a

                                 published entry

   arp_redefend_interval    -  Seconds to wait before defending a published

                                 entry

   arp_resend_interval      -  Number milliseconds between arp request

                                 retransmissions

IPSEC:

   ip_ipsec_integer_pads    -  Sets the type of pads used for block ciphers

   ip_ipsec_policy_interval -  Sets the interval between attempts to remove

                                 unused Security Policy rules.

   ip_ipsec_sa_interval     -  Sets the interval between attempts to remove

                                 unused Security Associations.

第30章 配置和管理ARPA/Bekeley

30.1 Internet服务

**30.1.1 ARPA服务**

telnet

ftp

ntp

gated #动态路由

**30.1.2 Bekeley**

rlogin hp0                #远程登录hp0主机

rcp hp0:/etc/profile        #拷贝hp0主机上的文件到本地房前目录                

remsh hp0 ll /etc        #在hp0之际上运行ll /etc

BIND

sendmail

rlpdaemon                 #管理远程打印

**30.1.3 r服务的安全性**

30.2 启动internet服务

30.2 启动internet服务

Internet服务启动进程：

1）启动服务守护进程：/sbin/init.d

2） 启动inet守护经常.

30.2.1 启动一个服务作为守护进程

30.2.2 通过Inetd启动

Example of inetd.conf：

#  grep -v &amp;apos;#&amp;apos; /etc/inetd.conf

ftp          stream tcp nowait root /usr/lbin/ftpd      ftpd -lv

telnet       stream tcp nowait root /usr/lbin/telnetd  telnetd -b /etc/issue

tftp        dgram  udp wait   root /usr/lbin/tftpd    tftpd

bootps      dgram  udp wait   root /usr/lbin/bootpd   bootpd

login        stream tcp nowait root /usr/lbin/rlogind  rlogind

shell        stream tcp nowait root /usr/lbin/remshd   remshd

exec         stream tcp nowait root /usr/lbin/rexecd   rexecd

ntalk        dgram  udp wait   root /usr/lbin/ntalkd   ntalkd

ident        stream tcp wait   bin  /usr/lbin/identd   identd

printer     stream tcp nowait root /usr/sbin/rlpdaemon  rlpdaemon -i

daytime      stream tcp nowait root internal

daytime      dgram  udp nowait root internal

time         stream tcp nowait root internal

echo         stream tcp nowait root internal

echo         dgram  udp nowait root internal

discard      stream tcp nowait root internal

discard      dgram  udp nowait root internal

chargen      stream tcp nowait root internal

chargen      dgram  udp nowait root internal

kshell stream tcp nowait root /usr/lbin/remshd remshd -K

klogin stream tcp nowait root /usr/lbin/rlogind rlogind -K

dtspc stream tcp nowait root /usr/dt/bin/dtspcd /usr/dt/bin/dtspcd

rpc xti tcp swait root /usr/dt/bin/rpc.ttdbserver 100083 1 /usr/dt/bin/rpc.ttdbserver

rpc dgram udp wait root /usr/dt/bin/rpc.cmsd 100068 2-5 rpc.cmsd

recserv stream tcp nowait root /usr/lbin/recserv recserv  -display :0

hacl-cfg    dgram   udp    wait    root  /usr/lbin/cmclconfd cmclconfd -p

hacl-cfg    stream  tcp    nowait  root  /usr/lbin/cmclconfd cmclconfd -c

registrar stream tcp nowait root /etc/opt/resmon/lbin/registrar /etc/opt/resmon/lbin/registrar

omni stream tcp nowait root /opt/omni/lbin/inet inet -log /var/opt/omni//log/inet.log

/etc/services # 记录端口的映射

安全化inetd:

# @(#)inetd.sec $Revision: 1.10.214.1 $ $Date: 96/10/08 13:20:06 $

#

#

# The lines in the file contain a service name, permission field and

# the Internet addresses or names of the hosts and/or networks

# allowed to use that service in the local machine.

# The form for each entry in this file is:

#

# &lt;service name&gt;   &lt;allow/deny&gt;  &lt;host/network addresses, host/network names&gt;

#

# For example:

#

# login         allow   10.3-5 192.34.56.5 ahost anetwork

#

# The above entry allows the following hosts to attempt to access your system

# using rlogin:

#               hosts in subnets 3 through 5 in network 10,

#               the host with Internet Address of 192.34.56.5,

#               the host by the name of &quot;ahost&quot;,

#               all the hosts in the network &quot;anetwork&quot;

#

# mountd      deny    192.23.4.3

#

# The mountd entry  denies host  192.23.4.3  access to the NFS  rpc.mountd

# server.

#

# Hosts and network names must be official names, not aliases.

# See the inetd.sec(4) manual page for more information.

dtspc   allow   127.0.0.1       loopback cschp77

第31章 主机名解析和域名服务

31.2 名字解析方式

**31.2 名字解析方式**

1)./etc/host

# The form for each entry is:

# &lt;internet address&gt;    &lt;official hostname&gt; &lt;aliases&gt;

#

# For example:

# 192.1.2.34    hpfcrm  loghost

#

# See the hosts(4) manual page for more information.

# Note: The entries cannot be preceded by a space.

#       The format described in this file is the correct format.

#       The original Berkeley manual page contains an error in the format description.

2).NIS

3).DNS

31.3域名系统介绍

**31.3.1 名字空间**

31.4.2 资源记录

31.7配置DNS客户端

**31.7** **配置** **DNS** **客户端**

31.7.1 配置名字服务器转换

**31.7.2 resolv.conf**

第32章NIS

32.1 NIS Concept

**32.1 NIS Concept**

32.1.1 NIS Domain

NIS ： network information system

NIS Domain setup:

1) domainname enviroment variable

2) /etc/rc.config.d/nameservs 中的 NIS_DOMAIN

**32.1.2 NIS** **映射**

        通过ypmake命令可将文件文件转换为dbm格式的数据。每个映射分别包含以.pag和.dir结尾的两个文件。

       Example:/etc/passwd别转换为以用户名的映射后 **，/var/yp** 目录会得到两个文件名为：passwd.byname.dir 和passwd.buname.pag

**32.1.3**

1）NIS主控服务器

2）NIS辅助服务器

3）NIS客户端

32.2 Configuring NIS

**32.2 Configuring NIS**

**32.2.1 Setting Up an NIS Domain Name**

1）domainname testdom

2）/etc/rc.config.d/namesvrs

       NIS_DOMAIN=testdom

**32.2.2 NIS Startup Files**

Server NIS processes are started at run level 2 using the /sbin/init.d/nis.server script.

The client processes are started using the /sbin/init.d/nis.client script.

Both of these scripts use variables in the /etc/rc.config.d/namesvrs file for their operation.

Typical entries for our testdom NIS server are shown next. Here we have set the host to run as master server and client for domain name testdom.

NIS_MASTER_SERVER=1

NIS_SLAVE_SERVER=0

NIS_CLIENT=1

NIS_DOMAIN=&quot;testdom&quot;

MAX_NISCHECKS=2

YPPASSWDD_OPTIONS=&quot;/etc/passwd -m passwd PWFILE=/etc/passwd&quot;

YPUPDATED_OPTIONS=&quot;&quot;

YPXFRD_OPTIONS=&quot;&quot;

**32.2.3 NIS Daemons**

NIS is an RPC-based service.  

However, if the RPC daemon is not running, it is started during the NIS startup process.

processes and daemons are found under the /usr/lib/netsvc/yp directory：

**32.2.4 Configuring the NIS Master Server**

32.2.5 Configuring an NIS Slave Server

32.2.6 Configuring an NIS Client

/etc/nsswitch.conf ：

passwd:       files nis

group:        files nis

hosts:        files dns

32.2.7 Testing NIS Configuration

For example, the following command lists maps for user names and passwords.

# ypcat passwd.byname

root:BCRwpNgfFq3Zc:0:3::/:/sbin/sh

daemon:*:1:5::/:/sbin/sh

bin:*:2:2::/usr/bin:/sbin/sh

sys:*:3:3::/:

adm:*:4:4::/var/adm:/sbin/sh

uucp:*:5:3::/var/spool/uucppublic:/usr/lbin/uucp/uucico

lp:*:9:7::/var/spool/lp:/sbin/sh

nuucp:*:11:11::/var/spool/uucppublic:/usr/lbin/uucp/uucico

hpdb:*:27:1:ALLBASE:/:/sbin/sh

nobody:*:-2:-2::/:

www:*:30:1::/:

dba:D2aLVIizQMwI6:102:101:,,,:/home/dba:/usr/bin/sh

boota:VUj3GoygfBOvA:103:20:,,,:/home/boota:/usr/bin/sh

#

If you see an output like this, your client and server are correctly configured. Try the same command on some other client on the network.

Table 32-5\. NIS Utilities Name  Function  

ypcat          Displays NIS maps  #显示NIS映射信息

ypinit          Builds and installs NIS map files #建立并安装NIS映射文件

ypmake          Rebuilds NIS tables  #重建NIS映射表

ypmatch          Matches and lists particular values in NIS tables  #匹配并列出NIS映射表中的特定值

ypset          Binds NIS clients to particular NIS servers  #将NIS客户端绑定到特定的NIS服务器上

ypwhich          Shows host names of NIS servers                          #显示NIS服务器主机名

32.3 Managing NIS

32.3 Managing NIS

32.3.1 Updating NIS Maps on the Master Server

# /var/yp/ypmake

will update NIS maps on master and slave servers

**32.3.2 Updating NIS Maps on a Slave Server**

# yppush  #Form NIS Master server

# ypxfr passwd.byname #From Slave Server

/var/yp cab be used with cron :

ypxfr_1perhour  This script should be invoked every hour.  

ypxfr_1perday  This should be invoked once per day.  

ypxfr_2perday  This should be invoked twice every day.  

**32.3.3 Changing a Password on a Client**

On NIS client :

#passwd

When you use this command, it contacts the rpc.yppasswdd daemon on an NIS server.

Updates its ASCII password file as well as the NIS maps.

On NIS Server:

# yppasswd

**32.2.4 Using rpcinfo**

The following command lists RPC services registered on NIS server myhp.

# rpcinfo -s myhp

The following command sends a UDP request to ypserv on host myhp.

# rpcinfo -u myhp ypserv

32.4 Controlling Access

第33章NFS

33.1 NFS概念

**33.1 NFS 概念**

**33.1.1 远程挂起的过程**

**33.1.2 NFS和RPC**

# cat /etc/rpc

##

# pragma VERSIONID &quot;@(#)rpc:    11R2-4&quot;

#       file of rpc program name to number mappings

##

rpcbind         100000  portmap sunrpc rpcbind

rstatd          100001  rstat rup perfmeter

rusersd         100002  rusers

nfs             100003  nfsprog

ypserv          100004  ypprog

mountd          100005  mount showmount

ypbind          100007

walld           100008  rwall shutdown

yppasswdd       100009  yppasswd

etherstatd      100010  etherstat

rquotad         100011  rquotaprog quota rquota

sprayd          100012  spray

selection_svc   100015  selnsvc

#

pcnfsd          150001  pcnfs

#

# NEW SERVICES ADDED AT 6.5

#

rexd            100017  rex

llockmgr        100020

nlockmgr        100021

status          100024

#

# SUN SUPPORTS THE FOLLOWING THAT HP DOES NOT @ release 6.5

#

3270_mapper     100013

rje_mapper      100014

database_svc    100016

alis            100018

sched           100019

x25.inr         100022

statmon         100023

bootparam       100026

ypupdated       100028  ypupdate

keyserv         100029  keyserver

tfsd            100037

nsed            100038

nsemntd         100039

ypxfrd          100069

nisd            100300  rpc.nisd

nispasswd       100303  rpc.nispasswdd

nis_cachemgr    100301

nisd_resolv     100302  rpc.nisd_resolv

automountd      100099

ttdbserver      100083

cmsd            100068  dtcalendar

**33.1.3 portmap/rpcbind**

**33.1.4 NFS** **版本**

33.2配置NFS服务器

**33.2.1生成/etc/exports文件**

Example：

root@cschp88 # cat /etc/exports

#/sysinfo -rw=glud02.nam.dow.com -root=glud02.nam.dow.com -access=glud02.nam.dow.com

#/usr/local/bin/unix_machines

##/var/opt/ignite/clients -anon=2

/var/opt/ignite/recovery/archives/cschp87 -anon=2,access=cschp87.sct.ucarb.com

/var/opt/ignite/recovery/archives/cschp86 -anon=2,access=cschp86

/var/opt/ignite/clients -anon=2

root@cschp87 # cat /etc/exports

#/sysinfo -rw=glud02.nam.dow.com -root=glud02.nam.dow.com -access=glud02.nam.dow.com

#/usr/local/bin/unix_machines

##/var/opt/ignite/clients -anon=2

/var/opt/ignite/recovery/archives/cschp88 -anon=2,access=cschp88.sct.ucarb.com

/var/opt/ignite/clients -anon=2

expotfs 读取/etc/exports文件并把这些条目拷贝到/etc/xtab文件中。

expotfs -a        #导出所有文件

exports -au        #收回所有导出文件

exports -u /usr/share/man #收回指定文件

33.2.2 在引导是启动服务器进程

/sbin/init.d以下3个脚本被执行：

1) nfs.core脚本在运行级别2别执行并且用在NFS客户和服务器上。他根据HP-UX版本启动不同进程：

HP-UX10.30或更低运行 portmap脚本；

HP-UX10.30或更高运行 rpcbind脚本.

2）nfs.client脚本在运行级别2的客户机上运行。

3）nfs.server脚本在一个NFS服务器的运行级别3别执行。

这些脚本在启动时使用/etc/rc.config.d/nfsconf文件中的配置参数。

33.2.3 启动一个NFS服务器并手工地导出到目录

                                                                                                                       33.2.4 查看导出和挂起的文件系统

root@cschp86 # showmount        #当前挂起本地文件系统的远程主机列表

CHHRGSUNIX001.dow.com

crnmr.nam.dow.com

crnmr1712.nam.dow.com

crossfire.nam.dow.com

cschp08.sct.ucarb.com

cschp86.sct.ucarb.com

cschp87.sct.ucarb.com

cschp88.sct.ucarb.com

csup01.sct.ucarb.com

glbck3.nam.dow.com

inova300.nam.dow.com

mdaxishsi.nam.dow.com

orasun02.nam.dow.com

proton.nam.dow.com

root@cschp86 # showmount -a                #列出由远程主机挂起的本地文件系统列表

CHHRGSUNIX001.dow.com:/spd/data/vms

crnmr.nam.dow.com:/spd/data/vms

crnmr1712.nam.dow.com:/spd/data/vms

crossfire.nam.dow.com:/spd/data/vms

cschp08.sct.ucarb.com:/spd/data/vms

cschp86.sct.ucarb.com:/spd/data/vms

cschp87.sct.ucarb.com:/spd/data/vms

cschp87.sct.ucarb.com:/var/opt/ignite/clients

cschp88.sct.ucarb.com:/var/opt/ignite/recovery/archives/clients

cschp88.sct.ucarb.com:/spd/data/vms

csup01.sct.ucarb.com:/spd/data/vms

glbck3.nam.dow.com:/spd/data/vms

inova300.nam.dow.com:/spd/data/vms

mdaxishsi.nam.dow.com:/spd/data/vms

orasun02.nam.dow.com:/spd/data/vms

proton.nam.dow.com:/spd/data/vms

33.3配置一个NFS客户机

**33.3** **配置一个NFS客户机**

HP-UX内核中必须配置NFS和LAN/9000子系统。

配置NFS客户机步骤：

**33.3.1 引导启动文件**

/sbin/init.d/nfs.core

/sbin/init.d/nfs.client

确保/etc/rc.config/nfsconf配置正确。

**33.3.2 /etc/fstab**

NFS_Server:/nfs/share/path        /local/path        nfs rw 0 0

NFS_Server:/nfs/share/path        /local/path        nfs rw 0 2

**33.3.3 挂起远程文件系统**

1)在启动时执行nfs.client脚本期间，NFS客户执行了mount -aQF nfs命令。如果你已经配置好了NFS客户比想重启系统，执行如下命令：

/sbin/init.d/nfs.core start

/sbin/ini.d/nfs.client start

2)如果NFS客户已经运行并且已经修改好了/etc/fstab,使用如下命令

# mount -aF nfs

3)/etc/fstab中没有配置

# mount NFS_server:/apps /opt/aaps

33.3.4 查看挂起的文件系统

# mount

33.3.5 查看由一个NFS服务器导出的文件系统

#mount -e NFS_Server

33.4NFS守护进程

33.5故障排查

33.5

ping

/etc/expots

/etc/fstab

processes

33.5.1 rpcinfo查看注册的rpc服务

1）

root@cschp86 # rpcinfo -s | grep -E &amp;apos;rpcbind|mountd|portmap|nfs&amp;apos;

   100000  2,3,4     udp,tcp,ticlts,ticotsord,ticots  rpcbind     superuser

   100005  3,1       tcp,udp                          mountd      superuser

   100003  3,2       udp                              nfs         superuser

-s Display a concise list of all registered RPC programs on host.  If host is not specified, it defaults to the local host.

2）

rpcinfo NFS_server #在客户端查看NFS服务端rpc服务注册情况

3）检测服务响应：针对特定服务发出TCP/UDP调用

root@cschp86 # rpcinfo -u cschp88 nfs

program 100003 version 2 ready and waiting

program 100003 version 3 ready and waiting

服务端接受NFS版本2/3的请求。

rpcinfo option

-d        删除一个特定程序的注册

-m        显示RPC操作的统计数据

-p        使用rpcbind的版本2来探测rpcbind

-s        显示一个短列表

-t        使用TCP做RPC调用

-u        使用UDP做RPC调用

33.5.2 nfsstat

nfsstat displays statistical information about the NFS (Network File System) and RPC (Remote Procedure Call), interfaces to the kernel.  It can also be used to reinitialize this information.  If no options are given, the default is

nfsstat -cnrs

That is, display everything, but reinitialize nothing.

Options:

-c 显示客户端信息

-s 显示服务端信息

-r 显示有关RPC的信息

-m 显示被挂起的文件系统信息

-z ony for root to reinitialize

第34章AutoMount

34.1 Automount 映射

34.1 Automount 映射

1）主Automount映射

2）直接Automount映射

3）间接Automount映射

4）特殊Automount映射

**34.1.1 主映射文件**

**34.1.2 直接映射**

**34.1.3 简介映射**

**34.1.4特殊映射**

34.1.5 其他映射

**34.1.6 automount进程**

34.2配置Automount

34.2 配置Automount

系统引导期间/sbin/init.d/nfs.client启动automount.

他从/etc/rc.config.d/nfsconf读取配置信息：

AUTOMOUNT=1

AUTO_MASTER=&quot;/etc/auto_master&quot;

AUTO_OPTIONS=&quot;-f $AUTO_MASTER&quot;

第35章 NTP

35.1NTP简介

35.1 NTP 简介

35.1.1 NTP时钟源

35.1.2 一些定义

35.2 配置NTP服务器

35.2 配置NTP服务器

/etc/rc.config.d/netdaemons

XNTPD:        Set to 1 to start xntpd (0 to not run xntpd)

/etc/ntpd.conf

35.3 配置NTP客户端

第36章 回顾

36.2syslog

**syslog** **守护进程：**

syslog守护进程配置文件/etc/syslog.conf

Form:

Seclector(选择器)：

       facility:决定了产生消息的子系统

       level:消息的严重级别

action(行为)

**Example of syslog.conf：**

36.3网络性能监控

netstat

nfsstat

lanadmin

36.4日常任务

system backup/recovry

performance monitor

log regenerate

Command

write

你可以用write 命令向当前登录到同一个系统的用户的终端发送信息。当你使用write时，write 会让你输入信息，每一次你敲回车，信息就会被传送到接收者的终端上，接收者可以向你回写信息，你可以通过你的终端进行交互的对话。当你完成键入信息后，敲入ctrl+d.就可以结束你的对话。

注意：除非你禁用这项功能，否则，在任何时候，别人都可以发送信息到你的终端。，如果这时你正在使用一个工具，如man,mail,或是一个编辑器的时候，一个用户给你发生一个信息，这行信息会出现在你的屏幕上，这会造成你的混乱。

如果你想要发送信息给一个用户，而这个用户当前没有登录系统，你会得到如下提示：

user is not logged on(用户没有登录系统)，其中user表示你试图发送信息的人的用户名

whereis

你可以用 whereis 命令来显示帮助的章节。例如：

$ whereis passwd

passwd :/sbin/passwd /usr/bin/passwd /usr/share/man/man.1.z/passwd.1

/usr/share/man/man4.Z/passwd.4

$whereis nothere

nothere:

这说明在章节 1 和 4 中有一个关于 passwd 命令的帮助条目，没有关于 nothere 的帮助手册。

mesg

你可以通过 mesg 命令来禁止其他用户发送信息到你的终端上。如果你给一个已经禁止接收其他用户发送信息的用户发送信息，你会接到 Permission Denied 错误（没有许可）。

mesg n 拒绝其他人 write 到你的终端。

mesg y 允许其他人 write 到你的终端。

mesg 报告是允许或是不允许其他人写到你的终端。

即使你的终端是禁止写入的 , 系统管理员一样能发送信息到你的终端。

news

系统中的所有用户都感兴趣的信息可以通过 news 命令广播出去。这个命令通常是系统管理员对系统中所有用户进行通告的时候，例如在系统关闭，备份时，或是在新的硬件生效时使用。

你可以键入 news 命令来阅读新闻。如果命令后没有选项，只有那些你还没有阅读过的信息会显示。

news 命令的选项有：

-a 读取所有的新闻，不管是否已经被读取过。

-n 只显示未读过的新闻的标题

每一个存取新闻的用户在他的 HOME 目录下都有一个 .news_time 文件。每一个 UNIX 系统中的文件都有一个时间标志，时间标志记录有上一次文件被修改的时间。 .news_time 上的时间标志会被更新，以匹配你最后读取得新闻信息的时间。如果一条新的新闻加入， news 命令知道这条新闻还没有被阅读，因为你的 .news_time 文件的时间标志比新的新闻的时间标志早

cat

注意 ： 如果文件包括控制字符，例如一个已编译的程序，你 cat 这个文件到你的终端，你的终端可能会失效。你可以用以下一种方法重新设置你的终端：

方法 1 ：

1\. 试图退出登录-回车后使用 exit 命令。

2\. 开关你的终端-关掉然后又打开。

3\. 重新登录-你能登录继续正常工作。

方法 2 ：

1\. 敲入 break 键。

2\. 同时按下 shift+ctrl+reset 。

3\. 回车

4\. Tset - e - k

5\. Tabs

另外，你的系统管理员可以终止你的终端对话。

printer

lp

lp 命令的语法是：

lp [ -dprinter] [-options] filename

例子：

$ lp report

request id kp-112 (1 file)

$lp - n2 memo1 memo2

request id is dp-113 (2 files)

$ lp - dlaster - t &quot; confidential &quot; memo3

request - d is laser - 114 (1 file)

$

第一个例子中，显示 lp 命令最简单的格式。我们将文件 report 送到系统默认的打印机。 lp 返回一个打印请求的 ID 和提交给队列的文件的个数。这里， 文件 report 已经被送到打印机&quot; dp &quot;，打印请求的 ID 号是 dp-112 。

在第二个例子中，我们我们送出两个文件 memo1 和 memo2 到打印机打印，同时我们想要两份拷贝（ -n2 ）。

在第三个例子中，你可以指定你的打印请求会被送到哪个打印机。打印的输出将被标题为&quot; confidentia 机密&quot;

lp [-d dest] [-n number] [-o option] - t title [-w] [file .]

一些 lp 命令的选项：

-nnumber 文件打印的重复的份数（默认是 1 ）。

-ddest 打印请求会被送到的打印机的名字。

-ttitle 在打印输出的标题页中打印标题。

-ooption 指定你的打印机的具体的选项，例如字体，间距，灰度，等等

-w 在文件打印完成以后，写一条信息到用户的终端。

在 lp （ 1 ） 中有一个选项的完整的列表。

lpstat

lpstat 命令

语法：

lpstat [-t]

* lpstat 报告你已经送往打印机队列的打印请求。

* lpstat - t 报告调度表的状态，默认的打印机名，设备，打印机状态，和所有的排队打印的请求。

lpstat 命令报告 lp 缓冲系统不同部分的状态。 lpstat ，当不加任何参数的时候，报告你当前送往打印的打印请求。

-t 选项显示系统中的所有的打印机的状态信息。

lpstat - t 命令告诉我们几个事情：

$ lpstat

rw-55 john 4025 Jul 6 14:26:33 1994

$

$lpstat - t

scheduler is running

system default destination: rw

device from rw: /dev/lp2235

rw accepting requests since Jul 1 10:56:20 1994

printer rw now printing rw-54\. Enabled sine Jul 4 14:32:52 1994

rw55 john 4025 Jul 6 14:26:33 1994 on rw

rw-56 root 966 Jul 6 14:27:58 1994

sheduler is running 调度表（ scheduler ）是一个程序，负责将你的打印请求送往正确的打印机。如果调度表没有运行，任何东西都不能打印。

system default destination ： rw rw 是默认的系统打印机的名字。如果你使用 lp 没有加上 - d printer 的选项，你的打印请求会被送到这台名叫 rw 的默认的打印机。 注意 你的默认的系统打印机可能有不同的名字（如 lp ）。

device for rw ： /dev/lp2235   　这表明打印机被联结到计算机的缓冲器。

printer rw now printing rw-55 ID 为 rw-55 的打印请求正在被打印。

enabled   　打印请求能够在 rw 上被打印。如果一个打印机是 disable 你可以提交请求，但是它们不会被打印直到打印机被 enabled 。

剩下的这些行是被打印的请求。这些字段列出请求的 ID ，排在哪个用户后打印，打印请求的大小，打印请求生成的时间。

cancle

cancel 命令

语法：

cancel id [id ]

cannel printer [ printer ]

例子：

取消一个由 lp 命令产生的打印任务。

$ cancel dp-115

取消当前在指定打印机上的打印任务

$ cancel laser

cancel 命令被用来从打印队列中删除打印请求。通过取消当前在打印机上的打印任务使下一个打印请求能被打印。你在打印非常长的文件或试图错误地打印一个二进制文件时（例如 /usr/bin/cat ），你可能会想要取消一个打印请求。请记住， lp 通常打印文本文件。、如果你没有指定合适的选项（例如 =oraw （图象打印）），打印其他类型文件的会使打印机混乱，并且会浪费许多的纸张。

要取消一个打印请求，你必须通过给 cancel 命令一个参数来告诉打印缓冲器那一个打印请求是你想要取消的。 cancel 的参数有两种类型：

* 一个请求的 ID （ lp 和 lpstat 给出的）

* 一个打印机的名字

通过赋予 cannel 一个打印请求的 ID ，指明的哪个打印请求就会被取消。如果你在 cancel 后面的参数是一个打印机名，当前在哪个打印机上正被打印的任务会被停止，打印队列中的下一个打印请求会开始打印。

$ lpstat

rw-113 mike 6275 Jul 6 18:46 1995

rw-114 mike 3349 Jul 6 18:47 1995

rw-115 mike 3258 Jul 6 18:49 1995

$ cannel rw-115

request &quot; rw-115 &quot; canceled

$ lpstat

rw-113 mike 6275 Jul 6 18:46 1995

rw-114 mike 3349 Jul 6 18:47 1995

$cancel rw

request &quot; rw-113 &quot; canceled

$lpstat

rw-114 mike 3349 Jul 6 18:47 1995

这个命令可以被任何用户执行以取消任何打印请求，你甚至可以取消其他人的打印请求；然而，被取消请求的用户会收到一个 mail ，告诉他谁取消了他的打印请求。系统管理员可以限制用户只能取消他们自己的请求。

management file&amp;directory

ls - l 　　　显示文件的特性

cat 　　　　　在屏幕上联结和显示文件的内容

more 　　　　格式化和在屏幕上显示文件的内容

tail 　　　　显示文件的结尾部分

cp 　　　　　拷贝文件或目录

mv 　　　　　移动或重命名文件或目录

ln 　　　　　链接文件名

rm 　　　　　删除文件或目录

lp 　　　　　将打印请求送到打印机排队打印

lpstat 　　　显示打印缓冲区的状态信息

cancel 　　　取消在打印队列中的打印请求

rm

rm 命令被用来删除文件。一旦文件被删除是不可挽回的， rm 命令至少要有一个参数（一个文件名），如果指定的文件名超过一个，所有的指明的文件都会被删除。

以下是最常用的选项：

-f 强制删除文件-用户不会得到任何提示，甚至在发生一个错误的时候。

-r 递归地删除指定目录中的所有的内容。

-i 询问或交互模式，它会要求用户确认来完成删除。你的回答有 y （ yes ）和 n （ no ），回车的作用和回答 no 是一样的。

注意 ： 通常是在极端的情况下才能使用 - r 选项。使用不正确，会删除你的所有的文件，一旦一个文件被删除，只能从备份磁带上恢复这个文件。如果你必须要用- r 选项，请和 -i

选项一起应用。

例如： rm - ir dirname

cp

-i （interactive）选项会在目标文件已经存在时给你警告，并要求你确认是否覆盖这个文件。

一个目录可以使用-r （recursive 递归）选项被拷贝

ls

使用 ls - l 输出的第一个字符表示文件类型。普通的文件类型包括：

* 普通文件

d 目录

l 链接文件

n 网络专用文件

c 字符设备文件（终端，打印机）

b 块设备文件（磁盘）

p 命名的管道（一种内部过程通信通道）

management privilege

chmod

r 读的权限

w 写的权限

x 执行的权限

和你如何更改权限：

+ 增加权限

- 减少权限

= 将权限设置为

你同时可以指明你想要修改哪一组的权限：

u 用户（文件的属主）

g 组（文件关联的组）

o 其他用户

a 所有用户（系统中的每个用户）

none 分配权限给所有的域

注释 ：想要禁止一个文件的所有的权限，键入以下的命令：

chmod = 文件名

POSIX shell

ESC

stty

HA

cmhaltnode/cmrunnode

cmviewcl -v

getconf

ioscan

root@cschp87 #  ioscan -funC disk

Class     I  H/W Path      Driver S/W State   H/W Type     Description

======================================================================

disk     12   0/0/1/0.2.0   sdisk CLAIMED     DEVICE       PIONEER DVD-ROM DVD-303 /dev/dsk/c0t2d0        /dev/rdsk/c0t2d0

disk    160  0/0/2/0.6.0   sdisk CLAIMED     DEVICE       SEAGATE ST318203LC        /dev/dsk/c1t6d0   /dev/rdsk/c1t6d0

disk    161  0/0/2/1.6.0   sdisk CLAIMED     DEVICE       SEAGATE ST318203LC        /dev/dsk/c2t6d0   /dev/rdsk/c2t6d0

disk      6   0/12/0/1.1.0  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d0   /dev/rdsk/c4t1d0

disk      7   0/12/0/1.1.1  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d1   /dev/rdsk/c4t1d1

disk      8   0/12/0/1.1.2  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d2   /dev/rdsk/c4t1d2

disk      9   0/12/0/1.1.3  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d3   /dev/rdsk/c4t1d3

disk     10  0/12/0/1.1.4  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d4   /dev/rdsk/c4t1d4

disk     11  0/12/0/1.1.5  sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c4t1d5   /dev/rdsk/c4t1d5

disk      0   1/4/0/1.0.0    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d0   /dev/rdsk/c6t0d0

disk      1   1/4/0/1.0.1    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d1   /dev/rdsk/c6t0d1

disk      2   1/4/0/1.0.2    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d2   /dev/rdsk/c6t0d2

disk      3   1/4/0/1.0.3    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d3   /dev/rdsk/c6t0d3

disk      4   1/4/0/1.0.4    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d4   /dev/rdsk/c6t0d4

disk      5   1/4/0/1.0.5    sdisk CLAIMED     DEVICE       HP      C5447A        /dev/dsk/c6t0d5   /dev/rdsk/c6t0d5

H/W Path：

A/B/C/X.Y.Z

数字A表示系统的一个总线号

数字X表示设备适配器在总线上的地址

数字Y为设备的设备号（优先级）

数字0为逻辑单元号

shell

|  To obtain:        |    Use the command:          |

| POSIX Shell        |  /usr/bin/sh ...              |

| Korn Shell        |  /usr/bin/ksh ...            |

| C Shell        |  /usr/bin/csh ...            |

| Key Shell        |  /usr/bin/keysh              |

| Bourne Shell        |  /usr/old/bin/sh ...          |

bdf &amp; df

newfs

netstat

netstat -in

ulimit

NAME

     ulimit - get and set user limits

talk

man

syntax hightlighting

man() {

 /usr/bin/man $* | \

   col -b | \

   vim -R -c &amp;apos;set ft=man nomod nolist&amp;apos; -

PAGER=&quot;pg -c&quot;

export PAGER

last/lastb

last        /var/adm/wtmp

lastb        /var/adm/btmp

diagnostic

stm

Support Tool Manager

XSTM -  the graphical interface (for X11-based graphics terminals)

MSTM -  the menu-based interface (for non-X11-based, non-graphics terminals)

CSTM -  the command line interface (for running scripts)

adb

adb, adb64 - absolute debugger

FileSystem

HP-UX File System:

1 、HFS=High Performance File System

2、VXFS

IBM：

JFS=Journaled File System

二者区别

1、hfs不带日志，vxfs带日志；

2、老的hpux使用hfs,新的hpux一般都是vxfs；

3、vxfs和hfs相比有许多优点；

4、IBM &amp;apos;s jfs=HP-UX &amp;apos;s vxfs;

建议使用vxfs，除了/stand文件系统。(注：/stand目录中存放系统内核，一般为vmunix类似的东西）。

Other File System:

1、NFS=Network File System

2、CDFS=CD-ROM File System

对于文件系统如何查看：

mount -v

/dev/vg00/lvol3 on / type vxfs ioerror=nodisable,log,dev=40000003 on Sat Jun 16 16:20:25 2012

/dev/vg00/lvol1 on /stand type vxfs ioerror=mwdisable,log,nodatainlog,tranflush,dev=40000001 on Sat Jun 16 16:20:27 2012

HP-UX file system type follow

$ fstyp -l

hfs

nfs

# fstyp -v /dev/vg00/oradata

vxfs

version: 5

f_bsize: 8192

f_frsize: 1024

f_blocks: 41943040

f_bfree: 1310869

f_bavail: 1228940

f_files: 351780

f_ffree: 327716

f_favail: 327716

f_fsid: 1073741833

f_basetype: vxfs

f_namemax: 254

f_magic: a501fcf5

f_featurebits: 0

f_flag: 16

f_fsindex: 9

f_size: 41943040

cdfs

autofs

cachefs

ffs

lofs

nfs3

procfs

vxfs

cifs

pipefs

fs_wrapper

NAME

     fs_wrapper - configuration and binary files used by file system

     administration commands

SYNOPSIS

     ff [-F FStype] ...

     fsck [-F FStype] ...

     fsdb [-F FStype] ...

     labelit [-F FStype] ...

     mkfs [-F FStype] ...

     mount [-F FStype] ...

     ncheck [-F FStype] ...

     newfs [-F FStype] ...

     quot [-F FStype] ...

     quotacheck [-F FStype] ...

     volcopy [-F FStype] .

newfs

makefs

fstpy

FileSystem

静态文件：（共享的文件）有三个重要的目录： /opt, /usr , /sbin

/opt 这个目录会用来存放应用程序和产品。开发人员和系统管理员会用它来安装新的产品和本地的应用程序。

/usr/bin 这个目录包含了基础的 UNIX 系统操作和文件处理的命令，所有的用户都有权限读取这个目录（ &quot;bin&quot; 是 binary 的缩写）。

/usr/sbin 这个目录中有所有的在帮助手册 1m 章节中的命令，这些命令都是系统管理命令。必须是超级用户才能使用其中的大多数命令。在帮助手册 1m 中有关于这些命令的文档。

/usr/lib 　　　　这个目录包括应用程序使用的文档和共享的库

/usr/share 　　　这个目录包括独立提供的文件（其中最重要的是帮助手册）

/usr/share/man 　这个目录包括所有的语在线帮助页有关的所有的文件。

/uar/local/bin 　这个目录通常用来存放本地开发的程序和工具。

/usr/contrib/bin 这个目录通常用来存放公用的程序和工具

/sbin 　　　　　　这个目录包括基本的用于启动与关闭系统的命令。

动态文件 （私有的文件）在这个节有七个重要的目录： /home, /etc, /stand , /tmp , /dev, /mnt , 和 /var;

/home 每一个 UNIX 系统的用户都有他或她自己的帐号

/etc 　　　　　 　这个目录中有许多的系统配置文件，这些文件在帮助手册的第四章节有说明文档。

/stand/vmUNIX 　　这个文件存储的是 UNIX 系统内核的文件。当系统启动时，这个程序被装载入内存，控制所有的系统操作。

/tmp 这个目录通常被操作系统的一个临时空间，通常是在操作系统创建中间文件，或是工作临时文件时使用。

注释： UNIX 系统的惯例：任何时间，任何以 tmp 为名的目录下的任何文件都可以被删除。

/dev 这个目录下有那些可以被联接到你系统中的硬件设备的文件，由于这些设备是作为一个到设备之间的联接，数据从来不会被直接存储到这些文件中，这些问文件通常被叫做特殊文 件或是设备文件。

/mnt 这个用来安装其它的设备 （例如：光驱）

/var/mail 这个目录包括每一个有邮件的用户的信箱。

/var/news 这个目录包括当前的新闻信息的所有的文件。他的内容可以通过键入 new -a 来显示。

/var/tmp 这个目录通常被用于用户的临时空间。

文件名字长度： 最大 14 个字符 最大 255 个字符， ( 如果长文件名支持 )

/etc/rc.config.d

system log

查看日志主要是查看关键字panic、warning、err等信息，如：

cat /var/adm/syslog/syslog.log |grep panic

cat /var/adm/syslog/syslog.log |grep warning

cat /var/adm/syslog/syslog.log |grep err

/etc/rc.log                                 /etc/rc 运行记录  

/etc/shutdownlog                       关机信息

/var/adm/syslog/syslog.log         一般系统运行日志

/var/adm/wtmp                          用户成功登录信息

/var/adm/btmp                          用户登录失败信息

/var/sam/log/samlog                   SAM日志

/usr/adm/diag/LOGxxx                用工具查看

/var/adm/nettl.LOG*                    网络日志

/var/adm/crash                           core dump文件

/var/adm/sw/swinstall.log             软件安装时的信息

/var/adm/sw/swremove.log            卸载软件时的信息

/var/adm/sw/swagent.log              swagentd daemon日志

/var/adm/sulog                            su用户转换的信息

/var/adm/syslog/mail.log               系统电子邮件的信息

Pack management

1.

在HP-UX系统上软件用Hewlett-Packand软件包发布器管理（通常叫做SD-UX）。

它不是一套命令和工具集，而是定义了如何对软件打包、捆绑、拷贝、安装和删除的系统。

SD-UX是基于IEEE软件发布标准的，它提供了很多用于安装、删除、列表和确认软件的命令。

SD=UX用于管理和发布操作系统、应用程序和HP-UX补丁。

在一个网络中，SD-UX可以用于建立一个集中的软件服务器。

SD-UX的主要功能：

安装软件

删除软件

列出已安装软件

确认已安装软件

拷贝和打包软件

配置软件

2.

SD-UX既可以用在GUI也可以用在TUI，通过命令行参数也可以不使用任何接口。

3.

软件包结构：

在SD-UX中软件被组织成一个部件或对象的层次结构。

这些部件是文件集、子产品、产品和包。

这些部件的存储位置叫做软件仓库。

文件集：一个文件集是文件和一些控制脚本的集合，是软件包层次结构中基本的条目。一个文件集只能属于一个产品但是它可以包含在很多子产品和包中。

子产品：如果一个产品包含多个文件集，最好把逻辑相关的文件集组合到一个子产品中。一个文件集可以是多个子产品的成员。

产品：产品是文件集和（或）子产品的超集。缺省时，SD-UX用于处理产品。

包：包一般由HP-UX打包用于软件的发布。包包含属于不同产品的文件集。一个产品不必再一个包中，因为包可以有不同产品的部分。与软件维护相关的操作可以在包上作为一个条目来完成。

软件仓库：软件仓库是文件集、产品和包的存放位置。一个软件仓库可以是用于发布软件的磁盘上的目录，如一个CD-ROM或磁带。缺省的软件仓库目录是/var/spool/sw。可以使用任何一个目录作为软件仓库，同一个服务器上为不同的应用程序提供多个软件仓库是可能的。

4.

列出已安装的软件：

swlist用于列出软件。

swlist -l bundel                      只列出包

swlist -l products                   只列出产品

swlist -l fileset                        列出文件集

swlist -d @ /var/spool/sw       列出软件仓库.var/spool/sw中的软件

swlist -l file X11                      列出所有X11产品中的文件

swlist -d @ hp1:/mydepot      列出主机hp1上名为mydepot的软件仓库中的软件

swlist也可以用于列出大小，修订本和开发商信息等属性。

5.

安装新软件：

swinstall用于软件安装。

根据你的终端类型，这个命令在文本或者图形接口中启动。

如果你想从一个特定的软件仓库安装，可以在命令行借助-s开关声明软件源。

例如，为了从一个磁带驱动器安装软件：swinstall -s /dev/rmt/0m

swinstall命令的所有动作都被记录在/var/adm/sw/swinstall.log文件中。

日志文件中包括一些标志：

========          表示一个任务的开始和或结束

ERROR             表示了一个导致不可能安装的严重错误

WARNING          表示虽然安装完成，但可能有一些错误

NOTE                 所有信息都放在这个标志下。大多数时候可以忽略这些消息

软件安装过程被swagentd守护进程控制。

如果这个守护进程没有运行，就不能开始软件的安装过程。

SD-UX守护进程在运行级2启动，如果你在一个单用户模式，就不能安装软件。

但可以使用命令启动守护进程：/sbin/init.d/swagentd start

HP-UX维护一个所有已安装软件的数据库（IPD）。

在分析阶段，swinstall使用这个数据库赖检查已安装的软件，swlist列出已安装软件。

swremove命令删除时，这个数据库升级来反映被删除的软件。

SD-UX命令负责维护这个保存在/var/adm/sw/products目录结构中的数据库。

6.

删除软件:

swremove命令用于从HP-UX系统删除软件。

它有着和swinstall相同的界面。

一旦软件删除开始，SD-UX检查相关的软件并删除所有在被选择的软件中且没有被其他任何产品和包使用的文件。

它通过删除软件来更新PID。

只通过删除软件所在目录并不能删除该软件，事实上，手工地删除这个目录可能导致问题。因为软件条目始终保持在PID中，尽管你已经删除了这个文件，但是系统认为它们仍然存在。当SD-UX检查相关软件时可能影响其它软件安装或删除过程。

软件的删除过程记录在/var/adm/sw/swremove.log文件中。

freedisk命令用于列出并删除已经很长时间没有使用的软件。在分析了文件集之后，该命令激活swremove命令来交互地删除包。

7.

确认以安装的软件：

swverify命令用于确认一个安装在系统中或软件仓库中的软件。

它检查文件的存在性和完整性及在一个软件包中的附属文件。包括执行软件的脚本。

当使用-d时，它操作一个软件仓库而非一个已安装软件。

如果软件确认成功它返回一个等于0的代码。

这个命令的日志记录在/var/adm/sw/swverify/log，它可以检查任何错误消息。

8.

管理软件仓库：

大型网络通过建立软件仓库避免在每台机器上使用安装安装介质。

软件仓库可以在磁盘上任何目录中创建。缺省软件仓库的位置是：/var/spool/sw。

磁带软件仓库可以使用swpackage命令创建。每次只能有一个命令可以访问磁带软件仓库。

swcopy -s /dev/rmt/0m @ /var/spool/sw       从一个磁带驱动器拷贝所有的产品到缺省软件仓库

swremove -d * @ /var/spool/sw                    从缺省的软件仓库中删除所有软件

swlist -d @ /dev/rmt/0m                                列出本地磁带中的内容

9.

HP-UX补丁：

给HP-UX操作系统或产品添加新的功能

添加对新硬件的支持

修补操作系统和应用程序的漏洞

补丁文件由PH开头，后面两个字符表示补丁类型：

命令补丁：其类型字段为CO

内核补丁：其类型字段为KL

网络补丁：其类型字段为NE

子系统补丁：其类型字段为SS（包括其他类型的补丁）

例如:PHCO_16423

10.

列出补丁：

swlist -l product PH*                                        #HP-UX 10.x

swlist -l patch &amp;apos;*.*,c=patch&amp;apos;   或 swlist -l patch        #HP-UX 11.00

安装和删除补丁：

获取补丁：HTTP或FTP下载等

unshare补丁：sh PHCO_15220

生成补丁仓库：swcopy -s PHCO_15520.depot PHCO_15520 @ /var/spool/sw

安装补丁：swinstall -s /var/spool/sw显示一个列表选择安装

删除补丁：同软件一样是借助swremove来完成的

11.SD-UX命令总结：

swinstall        安装软件

swremove        删除已安装软件;从仓库中删除软件

swlist                列出所有已安装或在仓库中的软件

swcopy                拷贝软件部件到软件仓库

swpackage        打包仓库中的软件

swreg                使软件仓库对于网络上的其他系统可见

swverify        确认已安装软件的完整性

swagentd        SD-UX守护进程

swagent        SD-UX代理

swacl                控制对软件的访问

swconfig        配置已安装的软件

LVM

pvcreate

mknode

mknod(1M)                                                         mknod(1M)

NAME

     mknod - create special files

SYNOPSIS

     /sbin/mknod name c major minor

     /sbin/mknod name b major minor

     /sbin/mknod name p

DESCRIPTION

     The mknod command creates the following types of files:

          +  Character device special file (first SYNOPSIS form),

          +  Block device special file (second SYNOPSIS form),

          +  FIFO file, sometimes called a named pipe (third SYNOPSIS form).

#mknod /dev/vglock/group c 64 0x010000

c指定group是字符设备文件

64是group设备文件的主编号，主编号始终是64

0xnn0000是group文件的十六进制形式的次编号，每个具体的nn必须在所有卷组中是唯一的

一般来说nn和卷组号对应比较容易识别，方便维护。

vgcreate

vgchange

lvcreate

#lvcreate -L 10240M -n lv_informix /dev/vglock   //10 G 的文件系统给逻辑卷增加大小

lvextend

#lvextend -l 50 /dev/vglock/lv_informix   ( 单位是页，页的大小再创建卷组时已经确定，不可以再更改，一般缺省为 4M ，所以是 200M)

或者

#lvextend -L 200 /dev/vglock/lv_informix ( 这是带大写的 L 参数，表示是以 M 为单位来分配的大小的。 )

System log

常用的日志文件：

文件名                        文件内容             监测方法

/etc/rc.log/etc/rc                运行记录             用读取文本文件的方法，

/var/adm/syslog/syslog.log   一般系统日志         注意提示信息及对应的

/var/adm/sw/*.log                软件安装日志       日期，分析发生的相关问题。

/var/adm/wtmp                  用户登录信息         用last命令查看

/var/adm/btmp                  用户登录失败信息   用lastb命令查看    

/var/sam/log/samlog           SAM日志                          

/var/spool/mqueue/syslog     sendmail日志                              

/etc/shutdownlog                关机(shutdown)信息

/usr/adm/diag/LOGxxx           用工具查看

/var/adm/nettl.LOG*             网络日志               由HP工程师负责

/var/adm/crash                   core dump文件           由HP工程师负责文件清理

getconf

getconf - get system configuration values

File system

/etc/rc.config

rc.config(4)                                                   rc.config(4)

NAME

     rc.config, rc.config.d/ - files containing system configuration

     information

SYNOPSIS

     /etc/rc.config

     /etc/rc.config.d/*

     /etc/TIMEZONE

notes

让进程在后台可靠运行的几种方法

[https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/](https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/)

Unix 技巧：让进程在后台可靠运行的几种方法

想让进程在断开连接后依然保持运行？如果该进程已经开始运行了该如何补救？ 如果有大量这类需求如何简化操作？

申 毅, 软件工程师, IBM 中国软件开发中心

2008 年 5 月 29 日

+

内容

我们经常会碰到这样的问题，用 telnet/ssh 登录了远程的 Linux 服务器，运行了一些耗时较长的任务， 结果却由于网络的不稳定导致任务中途失败。如何让命令提交后不受本地关闭终端窗口/网络断开连接的干扰呢？下面举了一些例子， 您可以针对不同的场景选择不同的方式来处理这个问题。

nohup/setsid/&amp;

场景：

如果只是临时有一个命令需要长时间运行，什么方法能最简便的保证它在后台稳定运行呢？

hangup 名称的来由

在 Unix 的早期版本中，每个终端都会通过 modem 和系统通讯。当用户 logout 时，modem 就会挂断（hang up）电话。 同理，当 modem 断开连接时，就会给终端发送 hangup 信号来通知其关闭所有子进程。

解决方法：

我们知道，当用户注销（logout）或者网络断开时，终端会收到 HUP（hangup）信号从而关闭其所有子进程。因此，我们的解决办法就有两种途径：要么让进程忽略 HUP 信号，要么让进程运行在新的会话里从而成为不属于此终端的子进程。

1\. nohup

nohup 无疑是我们首先想到的办法。顾名思义，nohup 的用途就是让提交的命令忽略 hangup 信号。让我们先来看一下 nohup 的帮助信息：

NOHUP(1)                        User Commands                        NOHUP(1)

NAME

      nohup - run a command immune to hangups, with output to a non-tty

SYNOPSIS

      nohup COMMAND [ARG]...

      nohup OPTION

DESCRIPTION

      Run COMMAND, ignoring hangup signals.

      --help display this help and exit

      --version

             output version information and exit

可见，nohup 的使用是十分方便的，只需在要处理的命令前加上 nohup 即可，标准输出和标准错误缺省会被重定向到 nohup.out 文件中。一般我们可在结尾加上&quot;&amp;&quot;来将命令同时放入后台运行，也可用&quot;&gt;filename 2&gt;&amp;1&quot;来更改缺省的重定向文件名。

nohup 示例

[root@pvcent107 ~]# nohup ping www.ibm.com &amp;

[1] 3059

nohup: appending output to `nohup.out&amp;apos;

[root@pvcent107 ~]# ps -ef |grep 3059

root      3059   984  0 21:06 pts/3    00:00:00 ping www.ibm.com

root      3067   984  0 21:06 pts/3    00:00:00 grep 3059

[root@pvcent107 ~]#

2。setsid

nohup 无疑能通过忽略 HUP 信号来使我们的进程避免中途被中断，但如果我们换个角度思考，如果我们的进程不属于接受 HUP 信号的终端的子进程，那么自然也就不会受到 HUP 信号的影响了。setsid 就能帮助我们做到这一点。让我们先来看一下 setsid 的帮助信息：

SETSID(8)                 Linux Programmer&amp;apos;s Manual                 SETSID(8)

NAME

      setsid - run a program in a new session

SYNOPSIS

      setsid program [ arg ... ]

DESCRIPTION

      setsid runs a program in a new session.

可见 setsid 的使用也是非常方便的，也只需在要处理的命令前加上 setsid 即可。

setsid 示例

[root@pvcent107 ~]# setsid ping www.ibm.com

[root@pvcent107 ~]# ps -ef |grep www.ibm.com

root     31094     1  0 07:28 ?        00:00:00 ping www.ibm.com

root     31102 29217  0 07:29 pts/4    00:00:00 grep www.ibm.com

[root@pvcent107 ~]#

值得注意的是，上例中我们的进程 ID(PID)为31094，而它的父 ID（PPID）为1（即为 init 进程 ID），并不是当前终端的进程 ID。请将此例与nohup 例中的父 ID 做比较。

3。&amp;

这里还有一个关于 subshell 的小技巧。我们知道，将一个或多个命名包含在&quot;()&quot;中就能让这些命令在子 shell 中运行中，从而扩展出很多有趣的功能，我们现在要讨论的就是其中之一。

当我们将&quot;&amp;&quot;也放入&quot;()&quot;内之后，我们就会发现所提交的作业并不在作业列表中，也就是说，是无法通过jobs来查看的。让我们来看看为什么这样就能躲过 HUP 信号的影响吧。

subshell 示例

[root@pvcent107 ~]# (ping www.ibm.com &amp;)

[root@pvcent107 ~]# ps -ef |grep www.ibm.com

root     16270     1  0 14:13 pts/4    00:00:00 ping www.ibm.com

root     16278 15362  0 14:13 pts/4    00:00:00 grep www.ibm.com

[root@pvcent107 ~]#

从上例中可以看出，新提交的进程的父 ID（PPID）为1（init 进程的 PID），并不是当前终端的进程 ID。因此并不属于当前终端的子进程，从而也就不会受到当前终端的 HUP 信号的影响了。

回页首

disown

场景：

我们已经知道，如果事先在命令前加上 nohup 或者 setsid 就可以避免 HUP 信号的影响。但是如果我们未加任何处理就已经提交了命令，该如何补救才能让它避免 HUP 信号的影响呢？

解决方法：

这时想加 nohup 或者 setsid 已经为时已晚，只能通过作业调度和 disown 来解决这个问题了。让我们来看一下 disown 的帮助信息：

disown [-ar] [-h] [jobspec ...]

       Without options, each jobspec is  removed  from  the  table  of

       active  jobs.   If  the -h option is given, each jobspec is not

       removed from the table, but is marked so  that  SIGHUP  is  not

       sent  to the job if the shell receives a SIGHUP.  If no jobspec

       is present, and neither the -a nor the -r option  is  supplied,

       the  current  job  is  used.  If no jobspec is supplied, the -a

       option means to remove or mark all jobs; the -r option  without

       a  jobspec  argument  restricts operation to running jobs.  The

       return value is 0 unless a jobspec does  not  specify  a  valid

       job.

可以看出，我们可以用如下方式来达成我们的目的。

灵活运用 CTRL-z

在我们的日常工作中，我们可以用 CTRL-z 来将当前进程挂起到后台暂停运行，执行一些别的操作，然后再用 fg 来将挂起的进程重新放回前台（也可用 bg 来将挂起的进程放在后台）继续运行。这样我们就可以在一个终端内灵活切换运行多个任务，这一点在调试代码时尤为有用。因为将代码编辑器挂起到后台再重新放回时，光标定位仍然停留在上次挂起时的位置，避免了重新定位的麻烦。

用disown -h jobspec来使某个作业忽略HUP信号。

用disown -ah 来使所有的作业都忽略HUP信号。

用disown -rh 来使正在运行的作业忽略HUP信号。

需要注意的是，当使用过 disown 之后，会将把目标作业从作业列表中移除，我们将不能再使用jobs来查看它，但是依然能够用ps -ef查找到它。

但是还有一个问题，这种方法的操作对象是作业，如果我们在运行命令时在结尾加了&quot;&amp;&quot;来使它成为一个作业并在后台运行，那么就万事大吉了，我们可以通过jobs命令来得到所有作业的列表。但是如果并没有把当前命令作为作业来运行，如何才能得到它的作业号呢？答案就是用 CTRL-z（按住Ctrl键的同时按住z键）了！

CTRL-z 的用途就是将当前进程挂起（Suspend），然后我们就可以用jobs命令来查询它的作业号，再用bg jobspec来将它放入后台并继续运行。需要注意的是，如果挂起会影响当前进程的运行结果，请慎用此方法。

disown 示例1（如果提交命令时已经用&quot;&amp;&quot;将命令放入后台运行，则可以直接使用&quot;disown&quot;）

[root@pvcent107 build]# cp -r testLargeFile largeFile &amp;

[1] 4825

[root@pvcent107 build]# jobs

[1]+  Running                 cp -i -r testLargeFile largeFile &amp;

[root@pvcent107 build]# disown -h %1

[root@pvcent107 build]# ps -ef |grep largeFile

root      4825   968  1 09:46 pts/4    00:00:00 cp -i -r testLargeFile largeFile

root      4853   968  0 09:46 pts/4    00:00:00 grep largeFile

[root@pvcent107 build]# logout

disown 示例2（如果提交命令时未使用&quot;&amp;&quot;将命令放入后台运行，可使用 CTRL-z 和&quot;bg&quot;将其放入后台，再使用&quot;disown&quot;）

[root@pvcent107 build]# cp -r testLargeFile largeFile2

[1]+  Stopped                 cp -i -r testLargeFile largeFile2

[root@pvcent107 build]# bg %1

[1]+ cp -i -r testLargeFile largeFile2 &amp;

[root@pvcent107 build]# jobs

[1]+  Running                 cp -i -r testLargeFile largeFile2 &amp;

[root@pvcent107 build]# disown -h %1

[root@pvcent107 build]# ps -ef |grep largeFile2

root      5790  5577  1 10:04 pts/3    00:00:00 cp -i -r testLargeFile largeFile2

root      5824  5577  0 10:05 pts/3    00:00:00 grep largeFile2

[root@pvcent107 build]#

回页首

screen

场景：

我们已经知道了如何让进程免受 HUP 信号的影响，但是如果有大量这种命令需要在稳定的后台里运行，如何避免对每条命令都做这样的操作呢？

解决方法：

此时最方便的方法就是 screen 了。简单的说，screen 提供了 ANSI/VT100 的终端模拟器，使它能够在一个真实终端下运行多个全屏的伪终端。screen 的参数很多，具有很强大的功能，我们在此仅介绍其常用功能以及简要分析一下为什么使用 screen 能够避免 HUP 信号的影响。我们先看一下 screen 的帮助信息：

SCREEN(1)                                                           SCREEN(1)

NAME

      screen - screen manager with VT100/ANSI terminal emulation

SYNOPSIS

      screen [ -options ] [ cmd [ args ] ]

      screen -r [[pid.]tty[.host]]

      screen -r sessionowner/[[pid.]tty[.host]]

DESCRIPTION

      Screen  is  a  full-screen  window manager that multiplexes a physical

      terminal between several  processes  (typically  interactive  shells).

      Each  virtual  terminal provides the functions of a DEC VT100 terminal

      and, in addition, several control functions from the  ISO  6429  (ECMA

      48,  ANSI  X3.64)  and ISO 2022 standards (e.g. insert/delete line and

      support for multiple character sets).  There is a  scrollback  history

      buffer  for  each virtual terminal and a copy-and-paste mechanism that

      allows moving text regions between windows.

使用 screen 很方便，有以下几个常用选项：

用screen -dmS session name来建立一个处于断开模式下的会话（并指定其会话名）。

用screen -list 来列出所有会话。

用screen -r session name来重新连接指定会话。

用快捷键CTRL-a d 来暂时断开当前会话。

screen 示例

[root@pvcent107 ~]# screen -dmS Urumchi

[root@pvcent107 ~]# screen -list

There is a screen on:

       12842.Urumchi   (Detached)

1 Socket in /tmp/screens/S-root.

[root@pvcent107 ~]# screen -r Urumchi

当我们用&quot;-r&quot;连接到 screen 会话后，我们就可以在这个伪终端里面为所欲为，再也不用担心 HUP 信号会对我们的进程造成影响，也不用给每个命令前都加上&quot;nohup&quot;或者&quot;setsid&quot;了。这是为什么呢？让我来看一下下面两个例子吧。

1\. 未使用 screen 时新进程的进程树

[root@pvcent107 ~]# ping www.google.com &amp;

[1] 9499

[root@pvcent107 ~]# pstree -H 9499

init─┬─Xvnc

    ├─acpid

    ├─atd

    ├─2*[sendmail]        

    ├─sshd─┬─sshd───bash───pstree

    │       └─sshd───bash───ping

我们可以看出，未使用 screen 时我们所处的 bash 是 sshd 的子进程，当 ssh 断开连接时，HUP 信号自然会影响到它下面的所有子进程（包括我们新建立的 ping 进程）。

2\. 使用了 screen 后新进程的进程树

[root@pvcent107 ~]# screen -r Urumchi

[root@pvcent107 ~]# ping www.ibm.com &amp;

[1] 9488

[root@pvcent107 ~]# pstree -H 9488

init─┬─Xvnc

    ├─acpid

    ├─atd

    ├─screen───bash───ping

    ├─2*[sendmail]

而使用了 screen 后就不同了，此时 bash 是 screen 的子进程，而 screen 是 init（PID为1）的子进程。那么当 ssh 断开连接时，HUP 信号自然不会影响到 screen 下面的子进程了。

回页首

总结

现在几种方法已经介绍完毕，我们可以根据不同的场景来选择不同的方案。nohup/setsid 无疑是临时需要时最方便的方法，disown 能帮助我们来事后补救当前已经在运行了的作业，而 screen 则是在大批量操作时不二的选择了。

HP-UX 基本命令学习(1)

HP-UX 基本命令学习 (1)

下面是查看 HP 小型机的信息的命令集：

**0** **、查看** **lun 的信息**

查看 磁盘 及其对应路径：

#ioscan -m dsf ? ioscan -fnC disk

查看划分过来的 lun

#ioscan -m lun

查看磁盘大小：

#diskinfo /dev/dsk/disk2 ? diskinfo /dev/rdsk/c*****

查看 HBA 卡的 wwn 和其他属性

#fcsmutil /dev/fclp0 ?

查看 XP 存储的磁盘

#/usr/contrib/bin/xpinfo -i    // 查看 xp 存储划分过来的磁盘

查看系统硬件配置情况 ---

#[/opt/ignite/bin]./print_manifest

1 、机型

#model

9000/800/L2000-44

注意：其中 44 是指每个 cpu 有 440MHZ 。

2 、 cpu 个数 (cstm- map-sel dev 19 -- info -- il --unselall ) cds 查看选择设备的状态

#top

CPU   LOAD   USER   NICE    SYS   IDLE BLOCK SWAIT   INTR   SSYS

0    0.02   0.0%   0.0%   0.%   0.0%   0.0%   0.0%   0.0%

1    0.00   0.6%   0.0%   0.%   0.0%   0.0%   0.0%   0.0%

2    0.00   2.% 97.0%   0.0%   0.0%   0.0%   0.0%

3    0.00   0.4%   0.0%   0.0% 99.6%   0.0%   0.0%   0.0%   0.0%

查看 cpu 的频率：

# echo itick_per_usec/D | adb -k /stand/vmunix /dev/kmem | awk &amp;apos;{print $2}&amp;apos;

查看内存大小

#/usr/sbin/dmesg | grep &quot;Physical:&quot;

physical page size = 4096 bytes, logical page size = 4096 bytes

查看交换分区的大小

#/usr/sbin/swapinfo -a

            Kb      Kb      Kb   PCT START/      Kb

TYPE      AVAIL    USED    FREE USED   LIMIT RESERVE PRI NAME

dev     4194304       0 4194304    0%       0       -    1 /dev/vg00/lvol2

reserve       - 311836 -311836

memory 3140508    8352 3132156    0%

查看 系统的位数 bits

#/bin/getconf KERNEL_BITS

64

#挂载光盘

ioscan -funC disk #查看光驱info

mount /dev/dsk/c1t0d0 /dvdrom # 挂载光驱

swinstall -i -s /dvdrom

安装补丁包：

把补丁包上传到 /tmp/path/2009Mar1131.depot

#swinstall -i -s /tmp/path/2009Mar1131.depot

查看补丁包是否安装成功情况：

#swlist |grep 2009Mar1131

2009Mar1131                   2009.03        HPUX 11.31 Megpatch for Mar 2009

查看补丁包的安装情况

#/usr/sbin/swlist -l patch

查看软件包的安装情况

#swlist -l bundle | grep ...

要确定系统上安装的产品及其版本，请使用 swlist 命令：

/usr/sbin/swlist -l product

3 、硬盘的大小信息

#diskinfo /dev/rdsk/c1t0d0

SCSI describe of c1t0d0:

            vendor: SEAGATE

        product id: ST39204LC

              type: direct access

              size: 8891556 Kbytes

  bytes per sector: 512

4 、硬盘的个数

#ioscan -funC disk

disk      0 0/0/1/1.0.0 sdisk CLAIMED     DEVICE       SEAGATE ST39204LC

                        /dev/dsk/c1t0d0   /dev/rdsk/c1t0d0

disk      1 0/0/1/1.2.0 sdisk CLAIMED     DEVICE       SEAGATE ST39204LC

                        /dev/dsk/c1t2d0   /dev/rdsk/c1t2d0

disk      2 0/0/2/0.0.0 sdisk CLAIMED     DEVICE       SEAGATE ST39204LC

                        /dev/dsk/c2t0d0   /dev/rdsk/c2t0d0

disk      3 0/0/2/0.2.0 sdisk CLAIMED     DEVICE       SEAGATE ST39204LC

                        /dev/dsk/c2t2d0   /dev/rdsk/c2t2d0

disk      4 0/0/2/1.2.0 sdisk CLAIMED     DEVICE       HP      DVD-ROM 305

                        /dev/dsk/c3t2d0   /dev/rdsk/c3t2d0

disk      5 0/4/0/0.8.0 sdisk CLAIMED     DEVICE       SEAGATE ST39236LC

                        /dev/dsk/c4t8d0   /dev/rdsk/c4t8d0

硬件地址的认识：

一个硬件路径 8/12.5.0 表示一个 SCSI 磁盘连接到系统。

数字 8 表示系统中的一个总线。数字 12 是 SCSI 适配器在总线上的地址。

这个磁盘连接到总线 8 ，总线转换器 5 ，设备号为 0 。

设备文件遵循 c#t#d#[ 选项 ] 的命名规则。 c# 数字代表接口卡实例号， t# 代表目标地

址， d# 代表逻辑单元

SCSI 目标地址

设备文件的&quot; t# &quot;部分确定这个设备文件相关联设备的 SCSI 目标地址。这个 SCSI

目标地址是通过设备自身上的跳线或者 DIP 开关来设置的。一个 SCSI 设备的硬

件路径的倒数第二个字符就是这个设备的 SCSI 目标地址。例如，在上例的 ioscan

输出中，在 8/12.3.0 的磁盘的 SCSI 地址为&quot; 3 &quot;。 8/12.6.0 这块磁盘的 SCSI 目标地

址为&quot; 6 &quot;。

SCSI 逻辑单元号

逻辑单元号（ LUN ）能够被用来识别一个磁带库的机器手，或者是一个磁盘阵列

的一个逻辑单元。对大多数的 SCSI 设备来说， LUN 号都是&quot; 0 &quot;。每一个 SCSI

设备的 LUN 号出现在设备硬件路径的最后一个小数点后。

设备存取选项

设备文件名的最后一部分是这个设备文件的存取选项。磁带机设备文件名可能有

多个选项。设备和设备的选项是不同的

# lssf /dev/rdsk/clt6d0 　　查看设备使用的驱动程序，设备的硬件地址，设备存取选项。

　　 disc3 card instance 1 scsi target 6 scsi LUN 0

　　 section 0 at address 52.6.0 /dev/rdsk/clt6d0

5 、查看操作系统版本和 license

#uname -a

HP-UX scp1 B.11.00 U 9000/800 1124961527 unlimited-user license

查看光纤卡的详细信息

rp5450#ioscan -funC fc

Class     I H/W Path Driver S/W State   H/W Type     Description

=================================================================

fc        0 0/4/0/0   td   CLAIMED     INTERFACE    HP Tachyon XL2 Fibre Channel Mass Storage Adapter

                     /dev/td0

rp5450#fcmsutil /dev/td0

                          Vendor ID is = 0x00103c

                          Device ID is = 0x001029

               XL2 Chip Revision No is = 2.3

           PCI Sub-system Vendor ID is = 0x00103c

                  PCI Sub-system ID is = 0x00128c

                              Topology = PRIVATE_LOOP

                            Link Speed = 2Gb

                    Local N_Port_id is = 0x000001

                      Local Loop_id is = 125

           N_Port Node World Wide Name = 0x50060b0000307f65

           N_Port Port World Wide Name = 0x50060b0000307f64

                          Driver state = ONLINE

                      Hardware Path is = 0/4/0/0

                Number of Assisted IOs = 1434

       Number of Active Login Sessions = 0

                  Dino Present on Card = NO

                    Maximum Frame Size = 960

                        Driver Version = @(#) PATCH_11.11: libtd.a : Jun 28 2002, 11:08:35, PHSS_26799

6 、如何查看内存

#dmesg |grep Physical

Physical: 4194304 Kbytes, lockable: 3134596 Kbytes, available: 3611312 Kbytes

7 、如何查看文件系统

#bdf

Filesystem          kbytes    used   avail %used Mounted on

/dev/vg00/lvol3    1025617   24790 898265    3% /

/dev/vg00/lvol1     700691   35482 595139    6% /stand

/dev/vg00/lvol8    2097152 436927 1557195   22% /var

/dev/vg00/lvol7    1048576 481524 531631   48% /usr

/dev/vg00/lvol6     255253     148 229579    0% /tmp

/dev/vg01/lv_tellin

                  2051553 127152 1719245    7% /tellin

/dev/vg00/lvol5    2097152   81783 1889462    4% /opt

/dev/vg01/lv_informix

                  2051553 413823 1432574   22% /opt/informix

/dev/vg00/lvol4     524288    1229 490375    0% /home

存在两个文件中： /etc/fstab   /etc/mnttab

8 、查看卷组、卷组所包括的逻辑卷、以及该卷组所包括的物理磁盘

#vgdisplay -v vg00

则结果都是按照逻辑卷组、逻辑卷、物理磁盘的顺序全部显示。

9 、查看卷组、逻辑卷的位置

#cd /dev/

在该目录下面有所有的逻辑卷组，再进入某个逻辑卷组，则看到它所有的所有

逻辑卷了。

10 、激活 / 去激活卷组

#vgchange -a y 卷组名 （激活）

#vgchange -a n 卷组名 （去激活）

11 、创建卷组、逻辑卷、文件系统的一系列命令

格式化

#pvcreate -f /dev/rdsk/c0t1d0   ( 这里假设有块盘的设备文件名是 c0t1d0)

#pvcreate -f /dev/rdisk/disk13   -f 是不管以前这块盘有没有作过 PV ，强制 PV 。危险动作，用时最好确认盘没加入 VG 里

     //pvcreate -B 创建一个用于镜像的可引导的 LVM 磁盘

创建卷组名

#mkdir /dev/vglock

创建卷组的设备文件名字

#mknod /dev/vglock/group c 64 0x010000 ( 这里注意 group 不能重复 )

创建卷组

#vgcreate /dev/vglock /dev/dsk/c0t1d0 （将物理磁盘 c0t1d0 加给该卷组）

#vgcreate -s 64 /dev/vglock /dev/disk/disk13 （将物理磁盘 c0t1d0 加给该卷组） 指定 pesize 64M

激活卷组

#vgchange -a y /dev/vglock

创建逻辑卷 lv_informix

#lvcreate -L 10240M -n lv_informix /dev/vglock   //10 G 的文件系统

给逻辑卷增加大小

#lvextend -l 50 /dev/vglock/lv_informix   ( 单位是页，页的大小再创建

卷组时已经确定，不可以再更改，一般缺省为 4M ，所以是 200M)

或者

#lvextend -L 200 /dev/vglock/lv_informix ( 这是带大写的 L 参数，表示

是以 M 为单位来分配的大小的。 )

如果还要将该卷组变为文件系统的话，那么如下创建文件系统

#newfs -F vxfs -o largefiles /dev/vglock/rlv_informix

创建文件系统挂接的目录

#mkdir /informix

将文件系统挂接上去

#mount /dev/vglock/lv_informix /informix

#vi /etc/fstab     // 增加一个文件自动挂载的条目

创建一个 VG

# vgscan -v             // 重建 /etc/lvmtab 文件，最好之前先备份 -----   vgscan -p -v   重新检查 vg ，不更新 lvmtab

# pvcreate -f /dev/rdsk/c6t0d0

# mkdir /dev/vg02

# mknod /dev/vg02/group c 64 0x030000

# vgcreate -s 32 vg02 /dev/dsk/c6t0d0 // 创建一个 PE size 为 32M 的 VG

创建条带化存储方式

# lvcreate -i 4 -I 64 -L 240 -n lv_name /dev/vg0X

-i 4 小写的 i ，表示要在 4 块磁盘 (PV) 上进行条带化

-I 64 大写的 I ，表示条带大小为 64KB

通过 fsadm 更改文件系统 largefiles 属性

# fsadm -F hfs -o largefiles /dev/vg02/rlvol1 或是

# fsadm -F vxfs -o largefiles /dev/vg02/rlvol1

取消 largefiles 属性

# fsadm -F vxfs -o nolargefiles /dev/vg02/rlvol1

查看文件系统等信息 ( 查看支持大文件系统 , f_flag: 16 为支持 )

# fstyp -v /dev/vg02/rlvol1

通过 vgscan 重建 /etc/lvmtab

在清除 VG 时，需要重建 lvmtab 里的信息。

# mv /etc/lvmtab{,.old}

# vgscan

如何扩文件系统：（ V3.31 ）

#bdf     查看文件系统对应的 lv

#lvextend -L 2048 /dev/vg00/lv04  

#fsadm -b 2048 /tmp

#bdf   验证文件系统扩展情况。

12 、删除卷组、逻辑卷

删除逻辑卷

#lvremove /dev/vglock/lv_informix

#lvremove -f /dev/vglock/lv_informix   强制删除，不需要回答 y/n

去激活卷组

#vgchange -a /dev/vglock ( 如果不能够去激活，则可以用如下命令强行去

激活， vgchange -c n /dev/vglock)

删除一个 vg

预删除卷组

#vgexport -p -s -m /tmp/vglock.map /dev/vglock

删除卷组

#vgexport -s -m /tmp/vglock.map /dev/vglock

#vgremove /dev/vglock   // 假如 VG 中还包含有 LV 的时候，删除不了。 只是在操作系统层的删除，不更新 lvmtab

vgremove: Volume group &quot;/dev/vglock&quot; still contains a logical volume(s).

vgremove: Couldn&amp;apos;t remove volume group &quot;/dev/vglock&quot;.

#vgexport vgdata1      // 删除 vg ， 更新 /etc/lvmtab ，删除相关的设备文件

-s scan 一般与 -p 用在一起

-p preview 预览，不 update lvmtab ，不删除 device

-m mapfile 文件输出，包括 vg 信息和 lv 信息

-f pvpaths 输出到文件

13 、创建共享卷组

在的一台已经创建卷组的机器上先去激活

#vgchange -a n /dev/vglock

预删除卷组

#vgexport -p -s -m /tmp/vglock.map /dev/vglock

将 map 文件传送到另外一台机器

#rcp scp1:/tmp/vglock.map scp2:/tmp/vglock.map

在另外一台机器上导入卷组之前要先创建卷组名

#mkdir /dev/vglock

创建 group 节点文件

#mknod /dev/vglock/group c 64 0x010000 ( 该节点一定要和第一台机器一致 )

导入卷组

#vgimport -s -m /tmp/vglock.map /dev/vglock

-s scan disk 并更新 lvmtab 。

按当前的 vg 更新 lvmtab

#vgscan -a

14 、做磁盘的 Mirror ，并进行磁盘更换

pvcreate -f -B /dev/rdsk/c2t2d0       // 预留启动分区

mkboot /dev/rdsk/c2t2d0

mkboot -a &quot; hpux -lq(;0) /stand/vmunix &quot; /dev/rdsk/c2t2d0

vgextend /dev/vg00 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol1 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol2 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol3 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol4 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol5 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol6 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol7 /dev/dsk/c2t2d0

lvextend -m 1 /dev/vg00/lvol8 /dev/dsk/c2t2d0

lvlnboot -r /dev/vg00/lvol3     （ root lv ）

lvlnboot -s /dev/vg00/lvol2     （ swap lv ）

lvlnboot -d /dev/vg00/lvol2     （ dump lv ）

lvlnboot -b /dev/vg00/lvol1     （ boot lv ）

lvlnboot -R                     (reserve 设为备用盘 )

setboot -a 0/0/2/0.2.0         （把这个盘的路径设为 alternate boot path ）

进入单用户维护模式：

在 10 秒中断时按任意健，然后键入 bo (enter), 然后提示是否进入 IPL 模式、选择 yes, 然后键入

hpux -is 进入单用户维护模式，然后

# vgchange -a y /dev/vg00     进行初始化 HP-UX 系统。

# lvchange -M n -c n /dev/vg00/lvol2         &lt; 给 mirror 作优化，把 swap 空间的 wmc 高速写缓存取消 &gt;;

# strings /etc/lvmtab                        &lt; 查看 Mirror 情况 &gt;;

# lvlnboot -v                              &lt; 查看 Mirror 是否做成功 &gt;;

# lvdisplay -v /dev/vg00/lvol1

解除镜像：

lvreduce -m 0 /dev/vg00/lvol1 /dev/dsk/c1t2d0

lvreduce vg00 /dev/dsk/c1t2d0

如果 mirror 无法作， stringe /etc/lvmtab 有多余的 PV, 要删除掉。 &lt; 慎用此命令，一定要备份

vgdisplay -v vg0x 信息 &gt;;

# vgreduce /dev/vg0x /dev/dsk/cxtydz

# lvremove /dev/vg01/lvol1            &lt; 删除 vg01 内 lvol1 卷 &gt;;

更换有镜像根盘的方法、步骤 :

# make_tape_recovery -Av

# shutdown -ry 0

Replace the bad disk

Bo&amp;#61664;y&amp;#61664;ISL&amp;#61664;hpux -ls

# vgchange -a y /dev/vg00

# mv /etc/lvmtab /etc/lvmtab.bak

# pvcreate -f /dev/rdsk/cxtydz

# mv /etc/lvmtab.bak /etc/lvmtab

# mkboot /dev/rdsk/cxytdz

# mkboot -a &quot; hpux -lq(;0) /stand/vmunix &quot; /dev/rdsk/cxtydz

# vgcfgrestore -n /dev/vg00 /dev/rdsk/cxtydz

# vgsync /dev/vg00

# lvlnboot -r /dev/vg00/lvol1

# lvlnboot -s /dev/vg00/lvol2

# lvlnboot -v

# shutdown -ry 0

更换有镜像硬盘的方法、步骤 :

# lvreduce -k -m 0

# lvremove

# vgreduce -f vg00

# vgcfgbackup /dev/vgxx                 &lt; 备份 vgxx 信息，默认存放在 /etc/lvmconf 下 &gt;;

如果 vg0x 丢失用：

# vgcfgrestore -n /dev/vg0x /dev/rdsk/cxtydz

# vgchange -a y /dev/vg0x

14 、 informix 的版本的收集

#su - informix

informix&gt;;onstat -

这样可以看到 informix 的版本。

15 、双机维护命令

在一台运行以下命令先将两个节点的 cluster 守护进程都拉起来，然后还会自动的将应用也拉起来。

cmruncl;

或者先在主机上运行双机的守护进程，再将备机节点加入，然后再来将应用制定在某个节点上运行，那么指定的节点就应该是主机。

cmruncl -n scp1;

cmrunnode scp2;

cmrunpkg -n scp1 -v scp_service;

查看双机的状态

cmviewcl -v ；

cmviewcl ;

cmquerycl;

cmviewconf;

双机切换

方法一：可以停止主机

cmhaltnode scp1

方法二：可以手工切换应用

cmhaltpkg -n scp1 -v scp_service( 将应用 scp_service 从 scp1 机器上停止运行 )

或者

su - tellin

stellin&gt;;kill_scp.sh

或者

su - informix

informix&gt;;onmode -kuy

主机切换后的节点要重新变为可以切换的节点，必需要运行如下命令

#cmmodepkg e -n scp1   -v scp_service   ( 应用 scp_service 可以下次再切回

scp1 节点 )

有时候为了诊断备机，特将备机设置为不可以运行应用的节点，如

cmmodepkg d -n scp1   -v scp_service ( 节点 scp1 上是不可以运行应用 scp_

service)

16 、双机的配置文件的位置

#cd /etc/cmcluster/   ( 双机守护进程的配置文件 cmcluster.asc)

#cd /etc/cmcluster/scppkg/ ( 双机的应用配置文件 scppkg.asc,control.sh,

scppkg.sh ，这三个文件中有一个文件是用来制定双机的浮动 IP 的 )

17 、双机维护命令的位置

#cd /usr/sbin/ ( 用 ls cm* 可以看到所有关于双机的执行命令 )

rp5450#ls cm*

cmapplyconf   cmgetconf     cmhaltpkg     cmmigrate     cmquerycl     cmrunpkg      cmstartres    cmviewconf

cmcheckconf   cmhaltcl      cmhaltserv    cmmodnet      cmruncl       cmrunserv     cmstopres

cmdeleteconf cmhaltnode    cmmakepkg     cmmodpkg      cmrunnode     cmscancl      cmviewcl

18 、双机的配置

》》》配置 cmcluster.asc;

检查 cmcluster.asc 配置文件的有效性

#cmcheckconf -v -C cmcluster.asc

如果配置不对，则会有错误提示，根据错误提示再来更正，

直到正确后才来应用该配置文件

#cmapplyconf -f -v -C cmcluster.asc

如果觉得应用后配置要重新更改，可以将配置文件删除

#cmdeleteconf -v -c scp1

#cmdeleteconf -v -c scp2

》》》配置应用文件 scppkg.asc,control.sh,scppkg.sh

检查三个文件的有效性

#cmcheckconf -v -P scppkg.asc

如果配置不对，则会有错误提示，根据错误提示再来更正，直到正确后才来应用该配置文件

#cmapplyconf -f -v -C scppkg.asc

如果觉得应用后配置要重新更改，可以将配置文件删除

#cmdeleteconf -v -c scp1

#cmdeleteconf -v -c scp2  

备注：这里所指的删除是在需要单机诊断双机的时候才会用到，否则不需要这么负责，只需要重新应用一下就可以了，原来的删不删除无所谓。

**18** **、网络的配置**

》》》首先网线一定要连接正确在给小型机配置网卡的时候一定要先确保网卡的驱动程序已经安装了，用以下的命令查看 .

#lanscan

如果看到的主用网卡和附加的网卡的状态都是 up 状态，则表示网卡都可用了。而且此时一定要知道那块卡用来做数据网卡，这块网卡应该是在安装 HP-UX 操作系统的时候就已经确定了，比如选择 lan0 来做主用数据网卡，并且该块网卡的地址一般在安装 HP-UX 的时候也已经显示了它的设备路径如： 0/1/10/0 等，或者用 lanscan 命令也可以看到它的路径，指导后就应该将直连网线从该网扣连接到主用 HUB 上去。然后另外两块是备用网卡，也可以根据设备的路径来确定他们两个的位置，确定以后就可以将其中一块卡用交叉网线与另外一台机器的同样的网口相连，用来做心跳线。那么另外的一个附加网卡就不要配置地址了，我们是用它来作为备用网卡使用的，要用直连网线从该口连接到备用 HUB 上，它既可以作为心跳网卡的备用网卡，也可以作为数据网卡的备用网卡。在 HPL2000 系列的机器上我们还可以看到在数据网卡的上面有一个网扣，该口是作为 console 口使用的，用一根 console 线可以与它相连接进行配置机器。

》》》再来配置 IP 地址

使用 sam 界面配置 网络参数或 SMH 配置菜单

#vi /etc/rc.config.d/netconf

配置： 主机名 网关 IP 地址 等。。。。

该文件下面有所有的网卡的名字、网卡的 iP 地址、网关、子网掩码的配置

这样配置以后可以长期生效，下次机器重新启动的时候就会根据该配置文

件来自动配置网络了。

或者

#ifconfig lan0 133.64.48.91 255.255.255.192

#ifconfig lan1 129.9.168.120 255.255.255.192

》》》查看网卡的地址

#lanscan lan0

#lanscan lan1

lan2 不配置地址。

》》》网卡的常用诊断工具

ping;

lanscan; 看看网卡地状态是否为&quot; up &quot; linkloop;( 用此命令的时候，一定要先用 lanscan 来查处网卡的物理地址，因为该命令的后面接的参数是网卡物理地址，这可以简单地断定网线、集线器是否有问题 )

》》》在同一网中， subnetmask 应一致。

19 、在配置双机的 cmcluster.asc 的时候要制定该网卡的 IP 地址所在的子网，则可以通过以下来查看

#netstat -in   （可以看到网卡的地址、 IP 地址对应的子网、网关、缺省路由、是否有浮动网卡、是否主机）

20 、配置路由信息

方法一：可以通过修改 /etc/rc.confg.d/netconf 文件来增加，下次启动的时候

就会生效。

方法二：可以用命令行来设置：

/usr/sbin/route   add default   20.08.28.98 1

21 、查看路由信息

#netstat -an

22 、配置远程维护

如何确定是否已经配置了远程维护，远程维护是通过硬件来配置的，只要远程维护的串口没有损坏，哪怕你是重新安装，在小型机前面板上的 remote 灯会亮为黄色，黄色的灯一直都是两着的表示可以远程维护串口正常。但是我们还是需要通过 GSP 来配置远程维护。

》》》小型机的 remote 口的配置

ctrl + b

enter

enter

GSP&gt;; ca

这样就出现了对话框，如果你要修改某个参数的话，可以通过该对话框来修改。

通常的值是：

bitrate :9600

flow control :software

terminal type:vt100

modem protocol:CCITT

modem bit rate:9600

flow control :hardware

mode transmit configuration:disable

mode presence:always connected

》》》 modem 上的配置

AT&amp;F

ATS0=1

AT&amp;WO&amp;Y0

保存退出。

备注： HP 公司一般提供了专门的全向 modem ，名字叫&quot;天幕驰舟&quot;，

modem 一定要接在 line 口上。

23\. 一个超级命令

#set_parms

它后面带的参数可以是如下

date_time: 设者时间；

ip_address ：设置网卡地址；

hostname ：设置主机名；

addl_network ：设置主机的网关。

24 、用户和用户组的添加

方法一：用 useradd 和 groupadd 命令来添加；

方法二：修改文件 /etc/passwd 和 /etc/group 文件来实现。

25 、一个有用的工具是 sam

通过 sam 可以进行各种操作，比如：用户、用户组的管理；逻辑卷组、逻辑卷的管理；内核参数的管理；

HP-UX 基本命令学习(2)

HP-UX 基本命令学习(2)

26?

一个有用的诊断工具mstm用它可以收集到所有的硬件信息，比如一共有哪些内存插口，每块现有的内存条有多大，还可以查几个内存条等等信息。 使用举例：

#mstm

选择system()，并且在菜单上选中Tools/information/information log

便可以看到很多关于硬件的消息，如：System Information for (scp1)

  HPUX Model Number......: L2000            //机器型号是HP L2000

  HPUX Model String......: 9000/800/L2000-44      

  Original Product Number: A5191A  

  Current Product Number.:

  System Serial Number...: (Unknown)

  Hversion...............: 0x5c40

  Sversion...............: 0x491

  Software Capabilities..: 0x100000f0PD CPU Information:

  Number of CPUs in the current Protection Domain = 2     //两个cpuCabinet 0; Cell 0; CPU Map

cpu -------------------------------------------------

slot |00|01|02|03|04|05|06|07|08|09|10|11|12|13|14|15|

    -------------------------------------------------

state| a| | | | | | | | | | | | | | | |

    -------------------------------------------------

    c - Configured                  (CPU powered on)

    d - De-configured               (CPU powered off)

    a - Active                      (configured and processes running)选择memory，并且在菜单上选中Tools/information/information log

便可以看到关于内存的信息，如：

-- Information Tool Log for MEMORY on path 8 --Log creation time: Wed Jul 3 17:05:47 2002Hardware path: 8

Basic Memory Description    Module Type: MEMORY

   Total Configured Memory   : 1024 MB   //可以看到总的内存有多少，是1G

   Page Size: 4096 Bytes    Memory interleaving is supported on this machine and is ON.Memory Board Inventory

  DIMM Slot      Size (MB)

  ---------      ---------

         0a            256            //可以看到每个内存槽里面是不是已经插了内存条，还有

                                         该内存条是多少的内存，比如这里0a槽上插的是256M

         1a            256

         0b            256

         1b            256

  ---------      ---------            //可以看出该台小型机的4个内存槽都已经插满了

  System Total (MB): 1024            

Memory Error Log Summary    The memory error log is empty.Page Deallocation Table (PDT)    PDT Entries Used: 0

   PDT Entries Free: 50

   PDT Total Size: 50在使用mstm的时候可以打开另外一个终端窗口，执行命令#/usr/sbin/ioscan -fn ，这样可以知道每个设备

的硬件地址信息。

这样可以得到如下结果：

lan        2 0/7/0/0   btlan6 CLAIMED INTERFACE HP A3738A PCI 10/100Base-TX Ultimate Combo

                          /dev/diag/lan2 /dev/ether2     /dev/lan2

memory      0 8            memory    CLAIMED     MEMORY       Memory

processor   0 160          processor CLAIMED     PROCESSOR    Processor

processor   1 166          processor CLAIMED     PROCESSOR    Processor

这样可以知道0/7/0/0地址对应的是一个100M的网卡，然后再到mstm窗口中去查看它的information log

信息，这样可以很清楚硬件信息了。

该收集结果文件中还可以找到磁盘的使用信息，如：    

I H/W Path   Driver      S/W State   Description  

====================================================================    

0 0/0/1/1.2.0 sdisk       CLAIMED     SEAGATE ST39204LC    

1 0/0/2/1.2.0 sdisk       CLAIMED     HP DVD-ROM 304    

2 0/3/0/0.0.0 sdisk       CLAIMED     HP C5447A    

4 0/3/0/0.0.1 sdisk       CLAIMED     HP C5447A    

6 0/3/0/0.0.2 sdisk       CLAIMED     HP C5447A    

8 0/3/0/0.0.3 sdisk       CLAIMED     HP C5447A    

10 0/3/0/0.0.4 sdisk       CLAIMED     HP C5447A    

12 0/3/0/0.0.5 sdisk       CLAIMED     HP C5447A    

3 0/6/0/0.1.0 sdisk       CLAIMED     HP C5447A    

5 0/6/0/0.1.1 sdisk       CLAIMED     HP C5447A    

7 0/6/0/0.1.2 sdisk       CLAIMED     HP C5447A    

9 0/6/0/0.1.3 sdisk       CLAIMED     HP C5447A    

11 0/6/0/0.1.4 sdisk       CLAIMED     HP C5447A    

13 0/6/0/0.1.5 sdisk       CLAIMED     HP C5447A  

Device     H/W Path   Product id    Size     Physical      Alternate         (Mbytes) Volume    Link        

====================================================================      

c1t2d0 0/0/1/1.2.0 ST39204LC       8683   yes bootable no      

c3t2d0 0/0/2/1.2.0 DVD-ROM            0   no            n/a      

c4t0d0 0/3/0/0.0.0 C5447A          1024   yes           no      

c4t0d1 0/3/0/0.0.1 C5447A          2052   yes           no      

c4t0d2 0/3/0/0.0.2 C5447A         10252   yes           no      

c4t0d3 0/3/0/0.0.3 C5447A          1024   no            n/a      

c4t0d4 0/3/0/0.0.4 C5447A          2052   no            n/a      

c4t0d5 0/3/0/0.0.5 C5447A         10252   no            n/a      

c5t1d0 0/6/0/0.1.0 C5447A          1024   yes           yes      

c5t1d1 0/6/0/0.1.1 C5447A          2052   yes           yes      

c5t1d2 0/6/0/0.1.2 C5447A         10252   yes           yes      

c5t1d3 0/6/0/0.1.3 C5447A          1024   no            n/a      

c5t1d4 0/6/0/0.1.4 C5447A          2052   no            n/a      

c5t1d5 0/6/0/0.1.5 C5447A         10252   no            n/a  

Note: All disk devices are listed here, not only hard disks.LVM mirroring software

**********************  

LVM mirroring software MirrorDisk/UX (B2491A) is NOT installed................................................................................

**********************

Part 2: VOLUME GROUPS

**********************

Volume Group: /dev/vg00

*************  

Physical Volumes:   /dev/dsk/c1t2d0  

Volume group disk space usage:  

Total    : 8676 Mbytes   2169 PE  

Allocated: 8404 Mbytes   2101 PE  

Free     :   272 Mbytes     68 PE  

PE size :     4 Mbytes

Volume Group: /dev/vg10

*************  

Physical Volumes:   /dev/dsk/c4t0d0   /dev/dsk/c5t1d0        Alternate Link  

Volume group disk space usage:  

Total    : 1020 Mbytes    255 PE  

Allocated:     0 Mbytes      0 PE  

Free     : 1020 Mbytes    255 PE  

PE size :     4 Mbytes

Volume Group: /dev/vg12

*************  

Physical Volumes:   /dev/dsk/c4t0d2   /dev/dsk/c5t1d2        Alternate Link  

Volume group disk space usage:  

Total    : 10248 Mbytes   2562 PE  

Allocated: 10076 Mbytes   2519 PE  

Free     :   172 Mbytes     43 PE  

PE size :     4 Mbytes

备注：其实用该收集工具就是在shell中执行不通的程序得到，如执行：

ioscan -fn;

mstm;

cstm;

sam;

等等。

27、重新启动机器

#reboot

#shutdown

28、关闭机器

#shutdown -hy 0

#init 0

28、unix的集中运行的模式

多用户模式，单用户模式等等6种。

用如下命令可以看看它的运行模式：

#who -r

29、普通的对话

#wall &quot;hello!&quot; (广播hello这个消息)

#banner &quot;hello!&quot;(放大hello这个消息)

#banner &quot;hello!&quot;|more (放大hello消息后再来广播它)

30、看当前的登录名

#logname

31、看所有登录用户

#whoiam

32、看登录用户在干什么

#whodo

33、看看进程

ps -ef|grep root (看root用户的进程，有时候console上执行的进程不能

够停止的话，那么就将console进程进程杀死，因为该进程是其它进程的

父进程。)

34、webconsole的设置

HP Secure Web Console 的配置与维护

  HP 的Secure Web Console 为系统管理员提供了一个基于Web的、更为 方便的接入Console的手段。系统管理员只需在任意一台能够ping通Web Console的PC上，启动网络浏览器，输入Web Console的IP，即可得到服务器Console的界面。

配置Web Console，应按以下步骤：

1)初始化Web Console：

1/将Web Console接入局网。其预设置的IP地址为192.0.0.192。

2/在您的PC上，运行以下命令：

       route add 192.0.0.192 Local_IP_address

3/确保能够ping 192.0.0.192。

4/在PC上运行网络浏览器，输入URL： [http://192.0.0.192](http://192.0.0.192) ，得到Web Console配置菜单。按菜单提示输入Admin Account 用户名和密码，将其IP改为本局网IP地址（确保IP不要重复）和子网掩码。

2)使用 Web Console

1/用普通Console的串口线，一端接服务器Local Console口，另一端接 Web Console 的串行口。

2/在PC的浏览器上，输入 Web Console当前的IP地址。即进入其LOGIN窗口，按要 求输入在配置时创立的Admin Account用户名和密码；则进入服务器Console界面， 用鼠标点击Access Console，黑色的Console窗口出现在屏幕右方；点击In/Out可放 大Console窗口。

35、demo进程的位置

/etc/rc3.d/中的文件在系统启动的时候便可以将进程拉起来。

36、磁带的使用

写：

tar cvf /dev/rmt/0m /temp/t.sql   //将temp目录下面的t.sql文件备份到磁带0m中；

读：

tar tvf /dev/rmt/0m   //读出磁带0m中的内容；从磁带上解开tar文件：

tar xvf /dev/rmt/0m/aa.tar ./     //将磁带上的aa.tar文件解开到当前目录下；当用磁带来启动机器的时候，我们在启动的时候敲击任意键，就可以进入启动的路径，

再输入SEA(search)来搜寻启动的路径，然后就可以找到磁带的路径，如磁带路径为5号路径，则输入po 5,便可以从磁带启动了。

37、HP-UX的安装

========================================================================

HP－UX双机系统的安装

1)在两台主机上分别安装好HP-UX操作系统，注意：在两台上的关于/，/stand，/var，/home，/usr，/opt，/swap，/dev等等文件系统的大小必须保持一致；

2)安装patch(以下的操作在两台主机上是一样的操作)

#mkdir     cdrom                       //创建一个DVD要挂接的目录

#ioscan    -kfnCdisk                //查看DVD的硬件描述文件，以便下面安装前的挂接

_____________________使用标识为support plus的光盘____________________

a)选择软件包中的标识为support plus的光盘插入DVD光驱中

#mount    /dev/dsk/c3t2d0 /cdrom       //将DVD文件系统挂接到/cdrom目录下

#cd       /cdrom

#ls                                     //浏览光盘，发现有XSWHWCR1100和XSWGR1100两个patch目录

#swinstall    -s   /cdrom/XSWHWCR1100         //这样就进入了sam中进行安装，选择光盘上的XSWHWCR1100，并且用sam中的菜单项Action下的子菜单Install来进行安装备注：安装完XSWHWCR1100这个patch之后，机器会自动reboot来重新创建新的内核

b)待机器再次启动之后，我们就可以安装同样的support plus这张光盘中的另外一个名叫XSWGR1100的patch了。

#mount    /dev/dsk/c3t2d0 /cdrom

#swinstall    -s   /cdrom/XSWGR1100        

备注：安装完该patch之后同样系统自动重新启动

__________________使用标识为3 of 4 Application Software光盘_______________

c)选择软件包中的标识为3 of 4 Application Software的光盘插入DVD光驱中

#mount    /dev/dsk/c3t2d0 /cdrom#swinstall -s /cdrom                     //进入sam后选择&quot;Ignite -UX-11-00    B.2.5.136    

                                         HP-UX   Installation Utilities for Installing

                                         11.00 System

                                         97186   HP-UX-B.11.00-32/4&quot;这个patch来安装

备注：安装完该patch之后同样系统自动重新启动

___________________使用标识为4 of 4 Application Software光盘____________

d) 选择软件包中的标识为4 of 4 Application Software的光盘插入DVD光驱中

#mount    /dev/dsk/c3t2d0 /cdrom#swinstall -s /cdrom   //进入sam后选择 揂.11.09     MC/ServiceGuard斦飧鰌atch来安MC/ServiceGuard

备注：安装完该patch之后同样系统也会自动重新启动

___________________使用标识为1 of 4 Application Software光盘____________

e)选择软件包中的标识为1 of 4 Application Software的光盘插入DVD光驱中

#mount    /dev/dsk/c3t2d0 /cdrom

#swinstall -s /cdrom    //进入sam后选择 ?3230A B.11.00 100Base-T PCI? 和揃.11.00 HP-UX Unlimited-User License斄礁鰌atch来安装。

                       //其中前一个patch用于安装附加网卡的驱动程序，只有安装了它，备用网卡和心跳网卡才在系统中可用，因为这两块网卡是系统附加的，必须要安装配套的驱动程序，其中53230A表示的是附加网卡的型号，这个可以从纸箱中的配件单上获取，系统本身自带的那块主用网卡是在安装操作系统的时候就已经自动被配置了，不用我们手工再配置了。

在未安装该patch之前，你用命令：

#lanscan则只能看到一块主用网卡；

在安装完该patch之后，你再用命令：

#lanscan则可以看到三块网卡。       //其中后一个patch用于安装无限制的license。

========================================================================

38、忘记了口令该怎么办

重新启动机器；

在启动的过程中按任意键，就会进入一个主菜单；

用SEArch来搜索启动的路径；

用bo + 路径的序列号来重起机器；

当出现Interactive with IPL (Y or N)?&gt;;时选择Y;

然后要求输入启动的内核的路径，hp_ux 0 (表示是启动到系统维护模式下面)

然后启动完成以后就可以进行passwd root来修改口令了。

39、如何做一个root的文件系统的全备份

#make_recovery -Av

40、光驱如何使用

#ioscan -funC disk

找到光盘的路径如/dev/dsk/c3t2d0

#mkdir /cdrom

#mount /dev/dsk/c3t2d0 /cdrom

#cd /cdrom

就可以了。

用完后将目录退出到根目录下面，再使用

umount /cdrom来释放光盘，便可以将光盘取出来。如果想从光盘启动的话，那么就重新启动机器，并且敲击任意键便进入SEA，再用po来制定光盘的

路径用光盘启动。41、从光驱上安装informix的几种类型的压缩文件

1)tar xvf /cdrom/IDS.tar;          (压缩文件是TAR类型的)

2) cpio -icvdBum &lt; /cdrom/IDS.CPI (压缩文件是CPI类型的)

42、双机配置必须两台机器都要配置的文件

/etc/hosts

/etc/services

/.rhosts

/etc/cmcluster/*

43、如何查看当前的网络子网、网络的掩码是多少

1）查看子网

#netstat -in

查看lan0对应的：

Name Mtu Net/Dest      Address        Ipkts Ierrs Opkts Oerrs Collis Queue

lan0 1500 172.0.8.0     172.0.8.68     3430395 0     1134355 0     0      0

可知子网就是172.0.8.02）查看掩码

查看/etc/rc3.d/netconfig.d/netconf文件中的netmasks字段就知道了。

44、如何创建数据库的DR

主机：ontape -s -L 0

     onmode -d primary online2_net(备机的网络数据库)

备机：ontape -p

     onmode -d secondary online1_net(主机的网络数据库)

45、HP-UX的文件系统

/     :根目录，以下的目录全部是子目录

/etc ：主要存放配置文件

/usr ：主要存放一般用户都可以执行的命令

/var ：主要存放unix核心

/usr/sbin ：主要是存放系统维护命令

/usr/bin ：主要是存放普通用户可以执行的命令

/home ：主要是作为普通用户的主目录

/opt ：主要是安装除了unix系统之外的应用程序

/swap ：交换区

/temp ：临时文件存放目录

46、如何在安装完HP-UX的OS操作系统之后，来打双机的patch呢？

#swinstall    -s   /cdrom/XSWHWCR1100 //先打CR

#swinstall    -s   /cdrom/XSWGR1100    //再打GR

再来安装第一张盘中的各个卡的驱动程序，以及安装unix用户的不受限制的协议

备注：安装完成以后用命令

swlist |grep 来查看有没有成功安装某个patch，如果觉得某个patch安装是错误的，不需要安装的话，那么可以用命令swremove -s 来进行删除。

47、如何安装cmcluster双机软件呢

一般都在软件包中的第4张盘，并且一定要找到license这张纸，上面又codeword，一定要输入codeword才能够看到该软件。如果该纸已经丢失了，那么可以从机器面板上找到序列号后再来网站

[http://www.license.hp.com](http://www.license.hp.com) 上去找。

48、日志文件的查询

/var/adm/syslog/syslog.log    //系统常用信息，如配置、修改、启动、关闭等信息

/var/adm/syslog/mail.log      //电子邮件信息

/var/adm/syslog/swinstall.log //软件安装产生的信息

/var/adm/syslog/swremove.log //软件卸载产生的信息

/var/adm/sulog                //执行su的情况

/var/adm/btmp                 //所有注册失败信息

/var/adm/vtmp                 //所有注册信息查看

日志主要是查看关键字panic、warning、err等信息，如：

cat /var/adm/syslog/syslog.log |grep panic

cat /var/adm/syslog/syslog.log |grep warning

cat /var/adm/syslog/syslog.log |grep err

49、如何配置系统的互相信任关系

在用户的主目录下面生成.rhosts文件，

如在smp01/smp02上的.rhosts文件中都输入：

smp01 root

smp02 root

50、如何从备份的磁带来恢复数据库informix呢

1)备份数据库（informix用户）

informix&gt;; ontape -s -L 02)从备份的磁带来恢复另外一台机器的数据库

informix&gt;; ontape -p

HP-UX 基本命令学习(3)

HP-UX 基本命令学习(3)

51、HP的网卡激活、去激活命令

#ifconfig lan0 up   //激活网卡lan0

#ifconfig lan0 down //去激活网卡lan0

备注：平时排除网卡的错误一般方法是：ping /ifconfig up|down /linkloop

52、HP L2000（for scp）双机配置的详细注解

安装操作系统，确定主机名字，确定root的口令，确定/、/usr、/var等文件系统的大小，选择

主用网卡，并且给主用网卡赋予IP地址；

打CR补丁，打GR补丁；

安装另外两个附加网卡的驱动程序，此时用ifconfig可以看到三块网卡都up了；

用直连线将两台机器的主用网卡都连接到主用的HUB上去；

给其中一个附加网卡赋予IP地址，此Ip地址与主用网卡的Ip地址是两个网段中的地址，并且用交叉线

将主备机的这个附加网卡连接起来，作为心跳线；

另外剩余的一个网卡不用赋予IP地址，它是作为主用网卡和心跳网卡的备用网卡，它不用给IP地址，

它的替用关系在双机配置文件cmcluster.asc文件中有指定，当主用、心跳网卡损坏的时候，它就会

去替换他们，并且获取他们的Ip地址；

最后安装cmluster双机软件，该软件安装的时候用swinstall -s /cdrom来安装，但是安装之前必须

要数据codeword，只有输入正确的codeword之后，才会看到该软件包，而codeword的获取是要根据

随机发的纸件中获取，或到 [http://www.license.hp.com](http://www.license.hp.com) 网站上获取，安装完后进入目录/usr/sbin下

检查有没有cmruncl/cmdeleteconf/cmapplyconf/cmhaltcl/cmrunnode/cmhaltnode等等文件；

创建锁盘逻辑卷组；

创建其它逻辑卷组、逻辑卷；

安装数据库；

安装tellin应用程序；

将双机配置文件拷贝到/etc/cmluster/目录下面进行配置、应用；

启动数据库；

启动应用；

启动双机；

53、HP N4000（for sdp）双机配置的详细注解

安装完操作系统，如同hp l2000一样；

安装一系列的包，并且安装FC60软件包；

将FC60上的三个sc10磁盘柜子中的磁盘划分成物理卷组LUN，如LUN0/LUN1/LUN2/LUN3等；

在LUN上创建锁盘逻辑卷组、其它逻辑卷组，在第一台上创建，在vgimport到第二台机器；

在的一台上激活其它逻辑卷组；

安装数据库；

再停止数据库；

将逻辑卷组在的一台机器上去激活；

在第二台机器上激活逻辑卷组；

在第二台机器上安装数据库文件系统；

从第一台机器上拷贝onconfig、sqlhosts、.rhosts、services等等文件到第二台机器上；

在第二台机器上直接oninit启动数据库；

在/etc/cmcluster/目录下面配置双机配置文件；

在/etc/hosts中加入逻辑机对应的逻辑IP；

将数据库中的sqlhosts文件的机器名改为逻辑机的名字或者改为浮动IP地址；

将逻辑卷组都去激活；

启动双机；

切换双机检验是否切换正常；

54、关于锁盘

1）锁盘的含义

锁盘是为双机系统出现某些特殊故障时确定主备用关系设置的，

因此每个节点在正常情况下都必须有权访问锁盘，因此也建议

用户不要将此盘为其它应用程序服务。为防止锁盘故障，锁盘

可配置多于一块，这时的要求同单块时一样，只是在配置文件

中需将所用锁盘都说明。在配置文件cmcluster.asc文件说明。

2）锁盘的物理盘

锁盘的物理磁盘必须有两个scasi磁盘接口与两台主机都要连接才行的。

安装于共享磁盘柜中。

锁盘是双机系统所必须的，而且必须采用共享磁盘形式。3）锁盘的逻辑卷组的创建

在TELLIN－SCP双机系统中，锁盘中不放置任何用户数据，

因此不需要进行逻辑卷的划分。若用户希望使用此盘空间，

可在不影响SCP双机正常工作的情况下根据自己的要求自行划分，双机对此没有附加要求。

在第一台机器上执行：

pvcreate /dev/rdsk/c0t2d0

vgcreate /dev/vglock /dev/dsk/c0t2d0

vgchange -a y /dev/vglock

vgdisplay                   //看看能不能够看到vglock这个磁盘卷组是激活的状态。

vgchange -a n /dev/vglock

vgexport -m -s /tmp/vglock.map /dev/vglock //将vglock卷组的创建信息到处到一个map文件中在第二台机器上执行：

rcp scp1:/tmp/vglock.map scp2:/tmp/vglock.map

mkdir /dev/vglock

mknod /dev/vglock/group c 64 0x010000

vgimport -m -m /tmp/vglock.map /dev/vglock

vgdisplay

vgchange -a y /dev/vglock

4）锁盘在双机运行重的状态

锁盘在双机启动之前应该在两台机器上都是去激活的状态，

即便是双机启动了，锁盘同样是去激活的状态。

55、关于双机cluster所使用的磁盘、以及应用package所使用的磁盘cmclustar.asc所使用的磁盘的数量多余于package所使用的磁盘。

56、FC60磁盘柜的维护命令集

57、如何启动scp系统

启动备机数据库

oninit

启动北极数据库

oninit

启动主机应用

manager

启动北极应用

manager

在主机上启动双机

mcruncl

58、如何启动sdp系统

因为sdp一般都是采用共享磁盘柜的形式，所以只需要

将共享磁盘在一台机器上运行cluster就行了：

cmruncl

它就会将informix和sdp等所需的逻辑卷组都激活，并且

将文件系统都挂接上，然后就cluster启动起来。

59、当数据库和cluster的主备不一致时，怎么恢复？

1）主用数据库运行scp1上,而应用程序的主用运行第二台机器上，这个时候只能将应用程序停止，然后将数据库都停止，将双机也停止。

2）然后将双机的配置文件删除，用命令cmdeleteconf来删除。然后再来生成配置文件，用命令cmapplyconf -C cmcluster.asc -P ./scppkg/scppkg.asc；

然后将刚才是主用的数据库启动起来并且将它变为standard状态，再在该台机器上做一个数据库的0级备份，然后将磁带拿到第二台机器上去恢复数据库，重新建立DR 关系之后，我们就可以将应用起来，然后将双机拉起来。此时数据库和双机的应用应该都一致。

60、hp小型机器第一次安装完操作系统之后，必须要修改的参数。

比如数据库参数，不修改的话就无法初始化数据库。

61、如何创建rootdg的系统备份（备份rootdg下面所有的东西）

＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

1)在一台好的机器上备份

#make_recovery -Av         //备份的是vg00卷组下所有的东西，比如/ ,/stand , /var ,/swap等等，备份放在了磁带上，下次若系统损坏了，可以用该磁带来启动并恢复系统。1)若用make_recovery 作备份的磁带来恢复的话，过程如下：

－－－－非交互式恢复系统

[1] 在磁带机中，插入系统恢复带

[2] Boot 系统

[3] 中断Boot 流程，进入 Boot_admin&gt;; 提示下

[4] Boot_admin&gt;; bo 8/16.0.0

8/16.0.0: 磁带机的 hardware path

[5] 选取 ?non-interactive ?

[6] 等待系统恢复完毕

－－－－－交互式恢复系统

[1] 在磁带机中，插入系统恢复带

[2] Boot 系统

[3] 中断Boot 流程，进入 Boot_admin&gt;; 提示下

[4] Boot_admin&gt;; bo 8/16.0.0

8/16.0.0: 磁带机的 hardware path

[5] 不选取 ?non-interactive ?[6] 选取

a. [ Install HP-UX ]

b. [   ] Advanced Installation

c. 配置或改变如下选项：

disks, file systems,

hostname, IP ddress,

timezone, root password,

DNS server, and gateway

[7] 选取 [install continue?]，直到系统恢复完毕               ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝62、如何更改HP的console终端的终端类型

A、进入缺省配置状态下面

现在关闭console的电源

control + d

然后在左手不松动的情况下打开电源

知道出现了提示说&quot;已经进入了缺省的设置&quot;，就放开左手，然后再打回车便可以进入缺省模式下面；B、进入configuration状态

先按住F8

再按住F10

然后用space空格键来进行选择修改，一般将终端类型选择为HP，但是也有时候选择vt100

修改之后按Esc退出键来进行保存退出，便可以了；

63、console其它各个参数的修改如果将我们诊断用户的故障电话进行分类，其中相当一部分的问题是出在Console的设置上。

通常的现象是Console上没有系统显示，或是键盘被锁住等。用户往往认为是主机的问题，

其实不然。下面我们简单介绍一下：

小型机控制台能正常运行的缺省配置是:

REMOTE MODE      ON(带* 号)

MEMORY LOCK     OFF(不带*号)

LINE MODIFY         OFF(不带*号)

MODIFY ALL          OFF(不带*号)

BLOCK MODE         OFF(不带*号)

查看上述配置的方法，如下：

在小型机控制台的键盘上方有一排功能键F1－F8，在功能键F4与F5之间有Menu和User System两个键。

当要查看小型机控制台的参数配置时，首先按User System键， 这时在小型机控制台屏幕的最下面一

行显示出8个高亮度的方块，每个方块从左到右分别对应功能键F1到F8；

再按功能键F4，表示选择Modes，依然是8个亮方块，但是方块上的文字改变了。依照上述5个参数的

名称检查相应的方块，看是否正确地配置了。如果没有，按与方块对应的功能键进行改变，直到所有

参数正确地配置好。最后按Menu键退出。

此外，这里介绍一种快速解决Console故障的方法：1）关闭Console电源

2）摁住CTL+D键，开Console电源，直到听到&quot;笛&quot;声，松开按键。

3）稍等片刻，在屏幕左下角将出现&quot;Default configs used, Press enter clear&quot;字样，按enter后一切恢复正常。

4）如果F4键位置的Remote Mode没有*号，摁F4加上*

以上做法实质上是为了恢复 Console缺省设置。

64、忘记了HP的口令该怎么办？

重启动机器到维护模式下面，更改后将模式再进入多用户模式就ok了：

1）重启，自检完成后，出现这一行&quot;To discontinue , press any key in 10 seconds&quot;,

这个时候按任意，系统终止启动，进入Main Menu&quot;

2）键入&quot;bo&quot;，在系统询问&quot;Interact with IPL（Y/N？）？&quot;时，输入&quot;y&quot;。

3）在提示符ISL&gt;;之后，输入&quot;hpux - is &quot;,系统进入单用户状态（即维护模式）

4)用passwd 更改口令

5）切换到多用户状态，用命令init 3,系统回复正常

65、HP：磁盘管理软件LOGIC VOLUMN MANAGER ，简称LVM，

它的修改卷组的用户和读写权限是用hpux 中的chown 和chmod来实现的。

补充：

初始化物理磁盘：pvcreate -f /dev/rdsk/c1t1d0

创建卷组：mkdir /dev/vglock

         mknod /dev/vglock/group c 64 0x0001

         vgcreate /dev/vglock   /dev/dsk/c1t1d0

查看卷组激活信息：vgdisplay /dev/vglock

激活卷组：vgchange -a -y /dev/vglock   (用vgchange -c   -y /dev/vglock来强制激活 )

去激活卷组：vgchange -a n /dev/vglock (用vgchange -c n /dev/vglock来强制去激活)

创建逻辑卷：lvcreate -L 500 -n lv_root /dev/vglock (-L是指定大小，单位 M)

           lvcreate -l 250 /dev/vglock (-l 是指页数，页单位4M)

创建文件系统：newfs -F hfs /dev/vglock/rlv_root

             mkdir     /informix

             mount   /dev/vglock/lv_root      /informix

扩展逻辑卷：lvextend -l 50 /dev/vglock/lv_root   (单位是页，页的大小再创建

           卷组时已经确定，不可以再更改，一般缺省为4M，所以是200M。)

           或者

           lvextend -L 200 /dev/vglock/lv_informix (这是带大写的L参数，表示

           是以M为单位来分配的大小的。)

扩展文件系统：umount /informix

             extendfs    /dev/vglock/lv_root  

             (如果是vxfs文件系统，则用

             extendfs -F vxfs /dev/vg00/lvol4)

             mount /dev/vglock/lv_root /informix导出逻辑卷组：vgexport   -p   -v   -m    /tmp/lock.map   /dev/vglock

             (将vglock逻辑卷组的信息导出,

删除逻辑卷组：vgexport -v -m /tmp/lock.map /dev/vglock （删除逻辑卷组vglock）              将该逻辑卷组导入导另外一套小型机上：

             rcp      scpn1:/tmp/lock.map scpn2:/tmp/lock.map

             在节点scpn2中，创建锁盘卷组目录名（取和scpn1节点相同的目录名）

             命令：# mkdir   /dev/vglock

             在scpn2节点上，为锁盘创建一控制文件名group

             命令：# mknod /dev/vglock/group c 64 0x0001

             最后一个参数oxhh0000应保证在scpn2节点中是唯一的，可能的话，

             其参数设置和scpn1节点 相同。为保证唯一性，可以如下命令检查已存在的卷组：

             在scpn2节点上，将锁盘配置从文件映射回系统

             命令：# vgimport -s -m /tmp/lock.map /dev/vglock    有时候还要指定 /dev/dsk/cxtxdx )

66、用 fbackup &amp; frecover灵活的备份所有mounted文件系统或者指定某个文件系统，

也可以用来恢复整个文件系统，也可以灵活的恢复某个指定的文件系统，比make_recovery -Av

要灵活一些，而且这两个命令恢复只需要在单用户模式下，而make_recovery这个命令要

重新用磁带启动来恢复整个rootdg.备注：与make_recovery的区别

make_recovery主要是备份rootdg的内容，用户恢复操作系统的；

fbackup &amp; frecover主要是用来备份所有的逻辑卷组中所有的mounted文件系统文件；

A、系统备份命令： fbackup1) fbackup的常用方式一：

[1]        进入单用户：

# init -s          或

# shutdown 0

[2]        系统全备份

# fbackup -f /dev/rmt/0m -0iv / -I /tmp/sysbk.index

-f : 设备文件名 ( such as DDS tape driver)

-i : 要包含的目录

-e: 不包含的目录

- I: 备份内容检索目录

- v: 备份内容详细列表

- 0 : 零级备份

# fbackup -f /dev/rmt/0m -i /   -e   /home

备份除了目录 /home的所有目录  

[3]        说明

a、该命令方式对系统当前mounted的文件系统进行备份

b、备份级别说明

备份级别有0～9个级别，如果当前系统采用零级备份，当下一次采用5级备份时，系统仅将会对有变化的文件进行备份。

2) fbackup的常用方式二：

〖1〗        # mkdir -p /tmp/fbackupfiles/index

# mkdir -p /tmp/fbackupfiles/log

〖2〗        # touch/tmp/fbackupfiles/index/full.`date&amp;apos;+%y%m%d.%H:%M&amp;apos;`

〖3〗进入单用户

# shutdown -y 0

〖4〗对系统进行全备份

# fbackup -0vi / -f /dev/rmt/0m \

-I /tmp/fbackupfiles/index/full.`date &amp;apos;+%y%m%d.%H:%M&amp;apos;` \

2 &gt;; /tmp/fbackupfiles/log/ full.`date &amp;apos;+%y%m%d.%H:%M&amp;apos;`

〖5〗说明

通过该方式可以知道系统备份需要的时间

3) fbackup的常用方式三：

〖1〗进入单用户

# shutdown -y 0

〖2〗对系统进行全备份

# fbackup -0uv / -f /dev/rmt/0m \

-g /tmp/fbackupfiles/mygraph \

-I /tmp/fbackupfiles/index/full.`date &amp;apos;+%y%m%d.%H:%M&amp;apos;` \

2 &gt;; /tmp/fbackupfiles/log/ full.`date &amp;apos;+%y%m%d.%H:%M&amp;apos;`

〖3〗说明

a、文件 mygraph: 包含需要备份的目录，格式如下：

/users/data

/home/app

e /oracle/sql

b、参数 u :

当备份系统成功时，系统将更新 /var/adm/fbackupfiles/dates.

4) fbackup的常用方式四：

备份远程系统

[1] 登录在本地系统时

# remsh backup_sysname &quot; fbackup -f DDS_sysname: /dev/rmt/0m -0vi / &quot;

[2] 登录在远程系统时

# fbackup -f backup_sysname: /dev/rmt/0m -0vi /  

5) fbackup的常用方式五：

压缩方式备份( 不建议使用、影响系统性能)

[1] 压缩方式备份

      # fbackup -0vi /dir -f - | compress | dd of=/dev/rmt/0m obs=10k

    &quot;－&quot; : 指向标准输出

[2] 查看备份内容

# dd if=/dev/rmt/0m ibs=10k | uncompress | frecover -I - -f -B、 系统恢复命令： frecover

1) 恢复磁带机上所有内容：

[1] 进入单用户:

# init -s or shutdown 0

[2] 恢复数据

# frecover -rf /dev/rmt/0m

恢复磁带上的所有数据

-f: 设备文件名      

-r: 恢复磁带上的所有数据

-I: 将磁带上文件索引存到指定的文件中

# frecover -I /tmp/index.txt -f /dev/rmt/0m

2) 恢复某一目录：

# frecover -xi /directory

# frecover -x -i /dir1 -i /dir2

# frecover -xoi /dir

-o: 覆盖/dir下已有的、相同名称的文件

# frecover -xvXi /dir

-X: 按磁带上目录恢复数据

# cd /tmp/local; frecover -xvYi /dir

-Y: 按磁带上文件名恢复数据

例如：

# cd /tmp/local

# frecover -xvF -i /home/filename

[恢复结果] /tmp/local/filename 不是 /home/filename

3)        从远程磁带机上恢复数据到本地：

# frecover -xi /dir -f remote_name : /dev/rmt/0m          

4)        从本地磁带机上恢复数据到远地系统：

# remsh remote_name &quot;frecover -xi /dir -f local_name:

/dev/rmt/0m&quot;

67、修改HP双机系统启动特性

HP机及SUN机型通常采用下述两种办法：HP机型：

修改配置文件：/etc/rc.config.d/cmcluster将其设为如下内容：

AUTOSTART_CMCLD=1。SCP 双机系统在主机启动时，不允许自动启动CLUSTER和其上的PKG，需要编辑

/etc/rc.config.d/cmcluster文件，使：

AUTOSTART_CMCLD=0

68、HP双机配置时，节点访问权限的配置

访问权限设置

在进行CLUSTER和PKG配置之前，要配置或修改访问安全文件，使每个节点有访问另一个节点的权限。

权限设置如下：

以root用户权限编辑（或创建）位于/etc/cmcluster目录下的cmclnodelist文件，使其包含如下内容：

scp1          root

scp2                    root

scp1            tellin

scp2            tellin

.rhosts

以root用户权限编辑根（/）目录下的.rhosts文件，使其包含如下内容：

scp1          root

scp2                    root

scp1            tellin

scp2            tellin

hosts.equiv

添加如下内容：

scp1          root

scp2                    root

scp1            tellin

scp2            tellin

69、HP小型机中内存与cpu的关系

一个cpu一般最多配置0.5G的内存，两个cpu配置1G的内存。

70、swapinfo查看交换区的使用情况，以及交换区的大小

scp1:/hptmp #swapinfo

            Kb      Kb      Kb   PCT START/      Kb

TYPE      AVAIL    USED    FREE USED   LIMIT RESERVE PRI NAME

dev     1048576       0 1048576    0%       0       -    1 /dev/vg00/lvol2

reserve       - 792332 -792332

memory   781512 318032 463480   41%

71、HP硬件收集工具的使用（适合于HP11。0版本和HP10。0版本）信息收集工具Info_col.xx和LVMcollect.xx使用方法：

a． 在需要进行收集的主机上建立一个目录：

# mkdir /tmp/hpce

b． 将收集工具info_col.xx和LVMcollect.xx传到需要进行收集的主机上的/tmp/hpce目录下：

如果主机使用的OS是10.xx，则使用info_col.10和LVMcollect.10的脚本;如果主机使用的OS是11.xx，

则使用info_col.11和LVMcollect.11的脚本。

可以使用ftp的方式（使用asc方式传送）传到主机，也可以使用磁带tar到主机。

c． 修改info_col.xx和LVMcollect.xx的执行权限。

# chmod 744 info_col.xx

# chmod 744 LVMcollect.xxd． 运行相应版本的info_col.xx进行信息收集工作。

对操作系统为10.xx的主机：

# cd /tmp/hpce

# sh ./info_col.10

对操作系统为11.xx的主机：

# cd /tmp/hpce

# sh ./info_col.11e． 系统提示输入相应的信息

输入操作者姓名

输入操作者员工号（可输入6个0）

输入产品型号（在主机贴的标签上可以找到--&quot;机器型号项&quot;）

输入产品序列号（在主机贴的标签上可以找到--&quot;序列号项&quot;）

       （注意：序列号一定要输入准确，请仔细核对）

确认输入的内容（选择&quot;y&quot;，系统开始自动进行信息收集）f． 等待自动收集程序运行结束，系统会在收集脚本执行的目录下（

通常为/tmp/hpce目录）生成一个ascii文件，文件名为&quot;&lt;序列号&gt;;.txt&quot;，此文件就是最后收集到的信

息文件。将此文件保存并传回即完成信息收集工作。

(备注：其实shell程序中使用的都是一系列的命令，如：ioscan -fn;mstm；sam等)

72、umask如何设置

当最初登录到系统中时， u m a s k命令确定了你创建文件的缺省模式。这一命令实际上和c h m o d命令正好相反。你的系统管理员必须要为你设置一个合理的u m a s k值，以确保你创建的文件具有所希望的缺省权限，防止其他非同组用户对你的文件具有写权限。在已经登录之后，可以按照个人的偏好使用u m a s k命令来改变文件创建的缺省权限。相应的改变直到退出该s h e l l或使用另外的u m a s k命令之前一直有效。

一般来说，u m a s k命令是在/ e t c / p r o f i l e文件中设置的，每个用户在登录时都会引用这个文件，所以如果希望改变所有用户的u m a s k，可以在该文件中加入相应的条目。如果希望永久性地设置自己的u m a s k值，那么就把它放在自己$ H O M E目录下的. p r o f i l e或. b a s h _ p r o f i l e文件中。如何计算umask值u m a s k命令允许你设定文件创建时的缺省模式，对应每一类用户(文件属主、同组用户、其他用户)存在一个相应的u m a s k值中的数字。对于文件来说，这一数字的最大值分别是6。系统不允许你在创建一个文本文件时就赋予它执行权限，必须在创建后用c h m o d命令增加这一权限。目录则允许设置执行权限，这样针对目录来说， u m a s k中各个数字最大可以到7。该命令的一般形式为：

umask nnn

其中n n n为u m a s k置0 0 0 - 7 7 7。

让我们来看一些例子。

计算出你的u m a s k值：

可以有几种计算u m a s k值的方法，通过设置u m a s k值，可以为新创建的文件和目录设置缺省权限。表1 - 8列出了与权限位相对应的u m a s k值。

在计算u m a s k值时，可以针对各类用户分别在这张表中按照所需要的文件/目录创建缺省权限查找对应的u m a s k值。

例如，u m a s k值002 所对应的文件和目录创建缺省权限分别为6 6 4和7 7 5。

还有另外一种计算u m a s k值的方法。我们只要记住u m a s k是从权限中&quot;拿走&quot;相应的位

表1-8 umask值与权限

u m a s k 文件目录

0 6 7

1 6 6

2 4 5

3 4 4

4 2 3

5 2 2

6 0 1

7 0 0

例如，对于u m a s k值0 0 2，相应的文件和目录缺省创建权限是什么呢？

第一步，我们首先写下具有全部权限的模式，即7 7 7 (所有用户都具有读、写和执行权限)。

第二步，在下面一行按照u m a s k值写下相应的位，在本例中是0 0 2。

第三步，在接下来的一行中记下上面两行中没有匹配的位。这就是目录的缺省创建权限。稍加练习就能够记住这种方法。

第四步，对于文件来说，在创建时不能具有执行权限，只要拿掉相应的执行权限比特即可。

这就是上面的例子，其中u m a s k值为0 0 2：

1) 文件的最大权限rwx rwx rwx (777)

2) umask值为0 0 2 - - - - - - -w-

3) 目录权限rwx rwx r-x (775) 这就是目录创建缺省权限

4) 文件权限rw- rw- r-- (664) 这就是文件创建缺省权限

下面是另外一个例子，假设这次u m a s k值为0 2 2：

1) 文件的最大权限rwx rwx rwx (777)

2 ) u m a s k值为0 2 2 - - - -w- -w-

3) 目录权限rwx r-x r-x (755) 这就是目录创建缺省权限

4) 文件权限rw- r-- r-- (644) 这就是文件创建缺省权限常用的umask值

表1 - 9列出了一些u m a s k值及它们所对应的目录和文件权限。

表1-9 常用的u m a s k值及对应的文件和目录权限

u m a s k值目录文件

022 755 644

027 750 640

002 775 664

006 771 660

007 770 660

如果想知道当前的umask 值，可以使用u m a s k命令：

第1章文件安全与权限11

如果想要改变u m a s k值，只要使用u m a s k命令设置一个新的值即可：

$ umask 002

确认一下系统是否已经接受了新的u m a s k值：

在使用u m a s k命令之前一定要弄清楚到底希望具有什么样的文件/目录创建缺省权限。否

则可能会得到一些非常奇怪的结果；例如，如果将u m a s k值设置为6 0 0，那么所创建的文件/目

录的缺省权限就是0 6 6！举例子：如何指定一个用户的umask值？73、xargs

在使用f i n d命令的- e x e c选项处理匹配到的文件时， f i n d命令将所有匹配到的文件一起传递

给e x e c执行。不幸的是，有些系统对能够传递给e x e c的命令长度有限制，这样在f i n d命令运行

几分钟之后，就会出现溢出错误。错误信息通常是&quot;参数列太长&quot;或&quot;参数列溢出&quot;。这就是

x a rg s命令的用处所在，特别是与f i n d命令一起使用。F i n d命令把匹配到的文件传递给x a rg s命

令，而x a rg s命令每次只获取一部分文件而不是全部，不像- e x e c选项那样。这样它可以先处理

最先获取的一部分文件，然后是下一批，并如此继续下去。在有些系统中，使用- e x e c选项会

为处理每一个匹配到的文件而发起一个相应的进程，并非将匹配到的文件全部作为参数一次

执行；这样在有些情况下就会出现进程过多，系统性能下降的问题，因而效率不高；而使用

x a rg s命令则只有一个进程。另外，在使用x a rg s命令时，究竟是一次获取所有的参数，还是分

批取得参数，以及每一次获取参数的数目都会根据该命令的选项及系统内核中相应的可调参

数来确定。

让我们来看看x a rg s命令是如何同f i n d命令一起使用的，并给出一些例子。

下面的例子查找系统中的每一个普通文件，然后使用x a rg s命令来测试它们分别属于哪类

文件：

下面的例子在整个系统中查找内存信息转储文件(core dump) ，然后把结果保存到

/tmp/core.log 文件中：

$ find . -name &quot;core&quot; -print | xargs echo &quot;&quot; &gt;;/tmp/core.log

下面的例子在/ a p p s / a u d i t目录下查找所有用户具有读、写和执行权限的文件，并收回相应

的写权限：

$ find /apps/audit -perm -7 -print | xargs chmod o-w

在下面的例子中，我们用g r e p命令在所有的普通文件中搜索d e v i c e这个词：

$ find / -type f -print | xargs grep &quot;device&quot;

在下面的例子中，我们用g r e p命令在当前目录下的所有普通文件中搜索D B O这个词：

$ find . -name \ ＊-type f -print | xargs grep &quot;DBO&quot;

注意，在上面的例子中， \用来取消f i n d命令中的*在s h e l l中的特殊含义。74、Top -s 300 -f     top.txt

为了防止有时候top不能查看到所有的进程,最好是等5分钟,并且将结果文件保存到文件中,这样再从文件中来

查看结果.

#### Open VMS {#open-vms}

#### Tru64/Digital Unix {#tru64-digital-unix}

psrinfo, pinfo - Displays processor administration information

sizer - Displays information about the system or kernel, or creates a system configuration file

vmstat - Displays virtual memory statistics

#### NonStop {#nonstop}