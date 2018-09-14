## Operating System {#operating-system}

#### AIX {#aix}

**系统错误日志**

**存放路径**：/var/adm/ras/errlog

**说明：**该日志记录了系统所检测到的软硬件故障和错误，尤其对系统的硬件故障有很大的参考价值，是AIX提供的最有价值的日志之一， errlog 文件用more或者其他文本的查看命令来打开我们看到的只是一对乱码，为了能够查看错误日志文件需要使用aix的errpt命令，如：errpt 列信息；errpt –a列详细信息，详细使用方法可以参考man，

**2、用户的登录日志**

**存放路径**：/var/adm/wtmp /var/adm/sulog

**说明：**这些日志记录了用户登录和访问服务器的情况信息，具体的日志文件有wtmp、、sulog等，它们记录的分别是不同的事件，wtmp记录的是历史的login和lognout信息，可以用last命令访问。sulog记录的是用户用su命令转变为另一用户的信息。who、last等这些命令可以查看wtmp和sulog的内容如：Last –f wtmp我们想查看最近10次登录的用户和他们的地址，可以用如下命令： last -10

**3、用户的失败登录日志**

**存放路径**：/etc/security/failedlogin

**说明：**这些日志记录了用户登录和访问服务器失败的情况信息，登录失败的情况单独记录在该日志中，可以用who命令来查看。

**4、集群管理软件hacmp的日志**

**存放路径**：/tmp/hacmp.out

**说明：**HACMP是IBM提供的确保系统运行可靠性的集群套件，HACMP在每次启动和关闭时都要经历一段时间以停止服务和转换文件系统，我们可以通过对HACMP。OUT日志文件的跟踪实时的了解HACMP在启动和关闭时的信息，如出现启动失败则可以帮助我们定位错误。

可以使用tail进行跟踪，tail –f /tmp/hacmp.out

**5、系统启动错误日志**

**存放路径**：/var/adm/ras/bootlog

**说明**：该日志可以跟踪系统在Boot过程中发生的问题，包括服务器液晶板上的代码信息都有记载。可以使用alog命令监视这些问题, 存放在/var/adm/ras/bootlog中，可以使用alog –o –t boot命令查看该文件。

**6、FTP用户操作日志**

**存放路径**：自定义（建议/tmp/ftplog.out）

**说明**：很多服务器都会用到FTP功能，大量的用户通过FTP登陆到服务器上给系统的安全性带来了很大的问题，AIX给我们提供了一套很不错的可以记录用户FTP操作情况的日志。

具体设置步骤如下：

在/etc/inetd.conf文件中编辑 FTP 一行，在FTPD后加“-d”

重启服务： refresh –s inetd

touch /tmp/ftplog.out

在/etc/syslog.conf文件中加上两行：

daemon:debug /tmp/ftplog.out

daemon:info /tmp/ftplog.out

重启服务： refresh –s syslogd

**7、crontab执行情况日志**

**存放路径**：/var/adm/cron/log

**说明**：主要是查看各用户crontab执行情况的日志。

|             |             |             |             |             |
| --- | --- | --- | --- | --- |
|             |             |             |             |             |
|             |             |             |             |             |
|             |             |             |             |             |
|             |             |             |             |             |
|             |             |             |             |             |
|             |             |             |             |             |
|             |             |             |             |             |

**AIX errpt 命令使用**

备查

修改当前的日志文件/usr/lib/errdemon -i /var/adm/ras/myerrlog修改当前日志文件大小/usr/lib/errdemon -s 28866

修改当前日志缓冲区大小/usr/lib/errdemon -B 20480修改2个重复错误之间的间隔时间/usr/lib/errdemon -t 50

ps -ef | grep errdemon

/usr/lib/errdemon

/usr/lib/errstopps -ef | grep errdemon

errpt | more

详细errpt -a | pg

以ASCII 方式显示

errpt -g -j 74533D1A | more

检查过去24小时内发生的错误日志date

errpt -a -s 0128092102

errclear 命令清除日志记录删除所有日志errclear 0

删除10天前的软件记录errclear -d -S 10

errpt -a

-a是以详细格式显示错误日资文件中的错误信息在系统中生成一个记录下来的错误报表

**aix的日志系统总结----------------------参考的 于宁斌《AIX 5L系统管理技术》**日志系统工作流程介绍1．一旦系统的某个功能模块检测到一个错误或定义的需要记录日志的事件，则记录到/dev/error设备，把它保存在NVRAM中，这样可以保证即使在系统崩溃的情况下也不会丢失最新的错误日志。2．同时，错误日志进程errdemon从/dev/error文件中读取错误日志，然后根据错误模版库（/var/adm/ras/errtmpit）和错误消息库（/usr/lib/nls/msg/＄LANGcodepoint.cat）对其进行处理后写入系统的错误日志/var/adm/ras/errlog中。错误日志进程由/usr/lib/errdemon命令启动，/usr/lib/errstop停止，默认是启动的。errdemon进程：从/dev/error逻辑设备文件中读取纪录，然后在系统错误日志中创建错误日志纪录，显然这才是重点。Errdemon的配置：/usr/lib/errdemon 命令可以启动errdemon进程，同样我们也可以通过使用参数来修改我们的errdemon,显然如果我们不是太了解还是系统初始的配置更适合我们！例如：/usr/lib/errdemon –s 20000 设定我们的日志文件大小为20000bytes最可能用到的可能就是-l参数了/usr/lib/errdemon –l# /usr/lib/errdemon -lError Log Attributes--------------------------------------------Log File /var/adm/ras/errlogLog Size 1048576 bytesMemory Buffer Size 16384 bytesDuplicate Removal trueDuplicate Interval 100 millisecondsDuplicate Error Maximum 1000上面显示我的错误日志文件是/var/adm/ras/errlog，这也是系统默认的错误日志的存放位置。具体其他的参数可以参看man 手册。使用方法大概介绍：查看错误日志:errpt命令用more或者其他文本的查看命令来打开errlog文件我们看到的只是一对乱码，为了能够查看错误日志文件需要使用aix的errpt命令。使用errpt命令查看日志,可能根据使用的参数来确定输出什么样的日志，甚至排序的方式，这是使用纯文本的日志不能做到的，或者说不能轻易做到的。下面我们来看errpt命令的使用。# errptIDENTIFIER TIMESTAMP T C RESOURCE_NAME DESCRIPTION9DBCFDEE 0109034400 T O errdemon ERROR LOGGING TURNED ON192AC071 0109034300 T O errdemon ERROR LOGGING TURNED OFFC092AFE4 0109033500 I O ctcasd ctcasd Daemon StartedA6DF45AA 0109033500 I O RMCdaemon The daemon is started.9DBCFDEE 0109033400 T O errdemon ERROR LOGGING TURNED ON192AC071 0106130900 T O errdemon ERROR LOGGING TURNED OFF369D049B 0106082400 I O SYSPFS UNABLE TO ALLOCATE SPACE IN FILE SYSTE这里的输出分为六列依次为：1．错误标示符IDENTIFIER：并不唯一，由它来确定使用的错误模板，显然同一种错误的IDENTIFIER是相同的。2．时间戳TIMESTAMP：错误发生的时间，MMDDhhmmYY,依次表示月日时分年。3．类型TYPE：错误的类型，或者说严重的程度。分为6个：PEND 设备或功能组件可能丢失 简写PPERF 性能严重下降 PPERM 硬件设备或软件模块损坏，确诊了的 PTEMP 临时性错误，经过重试后已经恢复正常 TINFO 一般消息，不是错误 IUNKN 不能确定错误的严重性 U4．种类CLASS c:指出错误源H 硬件或介质故障S 软件故障O 人为错误U 不能确定5． 资源名RESOURCE_NAME最初检测到错误的资源名软件或者硬件，并不代表这个资源有问题，而只是最先在它发现的。6．描述显示详细的日志信息# errpt -a|moreStandard input---------------------------------------------------------------------Standard inputLABEL: ERRLOG_ONIDENTIFIER: 9DBCFDEEDate/Time: Sun Jan 9 03:44:04 BEISSequence Number: 309Machine Id: 004250B94C00Node Id: ibm-5LClass: OType: TEMPResource Name: errdemonDescriptionERROR LOGGING TURNED ONProbable CausesERRDEMON STARTED AUTOMATICALLYUser Causes/USR/LIB/ERRDEMON COMMANDRecommended ActionsNONE其它指定日志文件 –I可以用来查看一个非errdemon指定位置的日志文件，例如某个日志文件备份。-t 参数，只显示-t参数指定的错误类型TYPE。-s 显示指定时间之后的日志文件.-d 指定种类CLASS.详细的参数只能看man 手册了# errpt -a -j 74533D1A# errpt -s 0108100100IDENTIFIER TIMESTAMP T C RESOURCE_NAME DESCRIPTION9DBCFDEE 0109034400 T O errdemon ERROR LOGGING TURNED ON192AC071 0109034300 T O errdemon ERROR LOGGING TURNED OFFC092AFE4 0109033500 I O ctcasd ctcasd Daemon StartedA6DF45AA 0109033500 I O RMCdaemon The daemon is started.9DBCFDEE 0109033400 T O errdemon ERROR LOGGING TURNED ON日志的清理errclear命令可以用来清理错误日志并且默认情况下cron会每天清理错误日志# crontab -l0 11 * * * /usr/bin/errclear -d S,O 300 12 * * * /usr/bin/errclear -d H 900 15 * * * /usr/lib/ras/dumpcheck &gt;/dev/null 2&gt;&amp;1显然，找上面的例子，S,O 类的错误会保留30天，而H的错误会保留90天errclear 0 删除多有记录errclear 7 删除7天以前的记录smit errclearsyslogdunix普遍用到的日志系统，配置文件/etc/syslog.conf没有什么多说的，比较普遍，定义的话是修改syslog.conf,保存的日志为文本格式syslog.conf配置文件格式信息类别.错误等级 记录的位置其中,各项的含义信息类别auth used by authorization systems (login)cron used for the cron and at systemsdaemon system/netword daemonkern produced by kernel messageslpr printing systemmail mail systemmark internally used for time stampsnews reserved for the news systemuser default facility, used for any programuucp reserved for the uucp system错误等级debug normally used for debugginginfo informational messagesnotice conditions that may require attentionWarning any warningserr any errorscrit critical conditions like hardware problemsAlert any condition that demand immediate attentionemerg any emergency conditionnone Do not send messages from the indicated facility to the selected file.记录的位置可以是本地的文件（包括设备文件如/dev/console）或远程syslog日志服务器。假如我要记录cron的所有错误信息，则可以在/etc/syslog.conf加入下面一行cron.err /var/cronerr.log定义记录cron的err信息到/var/cronerr.log文件

**进行AIX 的日常维护，需要关注哪些日志文件？** **解答:**

在进行AIX 的日常维护时，需关注的日志文件有：

|             |             |             |
| --- | --- | --- |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |
|             |             |             |

note

步骤 1 为用户创建账号：

# useradd -m  username  #创建账号

# passwd username  #设置密码

# pwdadm -c username  #清除用户的ADMCHK标志，用户登录时不强制更改密码

步骤 2 修改家目录权限：

# chmod 750 directory  

#其中750为设置的权限，可根据实际情况设置相应的权限，directory是家目录，一般为/home/username

步骤 3 如果新建用户要su到root执行系统管理和维护工作，则username必须加入system组。

先查询username所属组：

# id -Gn username

再添加用户所属组：

#chuser groups=group1,…,groupn,system username  #username请使用实际的用户名，group1,…,groupn请用用户以前的组名代替。

smit

geninstall -I &quot;a -cgNqX -J&quot;  -Z  -d /tmp/wood -f File 2&gt;&amp;1

root@seccs02:/&gt;installp  -d /tmp/wood all   

ref

/etc/inittab

AIX 中的inittab 文件（转）原文地址 [http://blog.chinaunix.net/u/20198/showart_437679.html](http://blog.chinaunix.net/u/20198/showart_437679.html)

/etc/inittab 文件控制着初始化过程。

/etc/inittab 文件为 init 命令提供脚本作为一个普通进程调度程序。构成 init 命令进程调度活动的主要（多数）进程是 /etc/getty 线进程（line process），发起（启动）专用线进程。被 init 命令特别调度的其他进程为后台进程（Daemon）和shell。

/etc/inittab 文件由 位置相关［position-dependent ］的条目组成，格式如下：

Identifier:RunLevel:Action:Command

每一个条目都被一个换行字符分隔。一个换行字符前面一个反斜杠 (\) 表示一个条目的延续。/etc/inittab 文件中的条目数目没有限制（而不是指条目的最大长度）。条目的最大长度是 1024 个字符。

条目字段有：

Identifier： 标识唯一对象的一个 1-4 位字符的字段。

RunLevel： 该条目运行的级别。

运行级别有下列属性：

  - 运行级别有效地符合系统进程的配置。

  - 由 init 命令启动的每一个进程都被分配一个或多个该进程可存在于之的运行级别。

  - 运行级别由 0-9 的数字来表示。例如，如果系统运行于级别 1，只有在运行级别字段有 1 的那些条目被启动。

  - 请求 init 命令改变运行级别时，条目中运行级别字段与目标运行级别不匹配的所有进程都会收到一条警告信号 (SIGTERM)，在进程被删除符号［kill signal (SIGKILL)］强行终止前，有20秒的宽限期。

  - 运行级别字段可为一个进程定义多个运行级别，可以0-9的任意组合。如果没有指定运行级别，进程假定在所有的运行级别有效。

  - 还有其他四个值会出现在运行级别字段，即使他们并不是真正的运行级别：a, b, c 和 h。在运行级别字段有这些字符的条目仅仅在telinit 命令请求时才运行（与当前的系统运行级别无关）。他们不同于init命令的运行级别，init命令永远不能进入a, b, c, h 运行级别。并且，所有这些进程的运行请求都不改变当前的运行级别。此外，init 命令改变级别时，由a, b, c 命令启动的进程并不断开（killed）。只有当 /etc/inittab 文件中他们的行在action字段标记为 off，他们的行从 /etc/inittab 文件中完全删除，或者init 命令进入单用户模式，这些进程才会被中断（killed）。

Action: 告知 init 命令如何处理在 process 字段指定的进程。init 命令可识别的 actions 如下：

 respawn： 如果进程不存在，则启动进程。却不等待进程终止（继续扫描 /etc/inittab 文件）。如进程死掉，则重启该进程。如进程存在，继续扫描 /etc/inittab 文件。

 wait： 当 init 命令进入匹配某条目的运行级别时，启动该进程并等待该进程的终止。当init命令处于同样的运行级别时，所有对 /etc/inittab 文件随后的读取都会导致 init 命令忽略该条目。

 once： 当 init 命令进入匹配某条目的运行级别时，启动该进程，并且不等待终止。当进程死掉时，也不重启该进程。当系统进入一个新的运行级别时，该进程仍然从之前运行级别的变化运行，程序也不重启。

 boot： 只在系统引导过程中运行的条目，这些进程是系统启动过程中，init 命令从 /etc/inittab 文件中读取的。启动该进程，不等待进程终止，并且进程死掉时，也不重启进程。有意义的指导依次为，运行级别应为默认，或者必须与系统引导时 init 命令的运行级别匹配。此 action 对于系统硬件重启后的初始化功能非常有用。

 bootwait： 系统引导后，init 命令从单用户到多用户状态，第一次运行的条目。启动该进程，并等其终止，进程死时，不重启该进程。如果 initdefault为 2 ，则系统引导后直接运行该进程。

 powerfail： 只有当 init 命令收到一个电源故障信号(SIGPWR)的时候，才执行与此条目相关的进程。

 powerwait： 只有当 init 命令收到一个电源故障信号(SIGPWR)的时候，才执行与此条目相关的进程。并等该进程终止，才继续处理 /etc/inittab 文件。

 off： 如果与该条目相关的进程当前正在运行，发送一个警告信号(SIGTERM)，然后等待 20 秒才用 kill 信号（SIGKILL）终止该进程。如果进程不在运行，忽略该条目。

 ondemand： 功能上与 respawn 相同，不过，此 action 应用 a, b, 或 c 值，而不用运行级别。

 initdefault： init 命令只在 最初调用时才扫描与此 action 相关的条目。如果存在，init 命令使用该条目来决定初始进入的运行级别。一般情况下，使用run-level 字段中指定的最高运行级别来作为初始状态。如果运行级别字段为空，则认作0123456789；因此，init 命令进入运行级别 9 。另外，如果 init 命令在 /etc/inittab 文件中找不到initdefault 条目，则在引导时向用户请求一个初始的运行级别。

 sysinit： 此类型的条目在登录前 init 命令正要访问控制台之前被执行。该条目只被用来初始化设备，init 命令可能会针对这些设备询问运行级别。这些条目被执行，并等待完成后才继续。

Command： 可执行的壳（shell）命令。整个 command 字段以 exec 为前缀，并传给一个 forked sh成为 sh -c exec 命令。任何合法的 sh 命令语法都可出现在该字段。并可用 # 插入注释。

getty 命令覆写 /etc/inittab 文件中出现在它之前所有命令的输出。要在引导日志中记录这些命令的输出，可输送这些输出到 alog -tboot 命令。

当 init 命令正在处理 inittab 条目时，stdin, stdout, 和 stderr 这些文件描述符（file descriptors）可能是不可用的。所有写入 stdout 或 stderr 的条目不起作用，除非把输出重定向到一个文件或者到 /dev/console。

下列命令是唯一支持在 /etc/inittab 文件中修改记录的方法：

mkitab： 把记录添加到 /etc/inittab 文件。

lsitab： 列出 /etc/inittab 文件中的记录。

chitab： 修改 /etc/inittab 文件中的记录。

rmitab： 从 /etc/inittab 文件中删除记录。

例如，想在 /etc/inittab 文件中添加一条记录，以运行级别2（run level 2）运行 find 命令并使之一旦完成就再次启动。

1\. 运行 ps 命令，只显示包含 find 的进程：

# ps -ef | grep find

root 19750 13964 0 10:47:23 pts/0 0:00 grep find

#

2\. 使用 mkitab 命令，在 /etc/inittab 文件中添加一个名为 xcmd 的记录：

# mkitab &quot;xcmd:2:respawn:find / -type f &gt; /dev/null 2&gt;&amp;1&quot;

3\. 使用 lsitab 命令显示新记录：

# lsitab xcmd

xcmd:2:respawn:find / -type f &gt; /dev/null 2&gt;&amp;1

#

4\. 查看进程：

# ps -ef | grep find

root 25462 1 6 10:56:58 - 0:00 find / -type f

root 28002 13964 0 10:57:00 pts/0 0:00 grep find

#

5\. 取消 find 命令进程：

# kill 25462

6\. 查看进程：

# ps -ef | grep find

root 23538 13964 0 10:58:24 pts/0 0:00 grep find

root 28966 1 4 10:58:21 - 0:00 find / -type f

#

本例中，由于 action 字段被配置 respawn，故而每一次该命令一完成，一个新进程就会启动。

该进程将继续再生 （re-spawning），除非修改 action 字段，例如：

1\. 把记录 xcmd 的 action 字段由 respawn 修改为 once：

# chitab &quot;xcmd:2:once:find / -type f &gt; /dev/null 2&gt;&amp;1&quot;

2\. 查看进程：

# ps -ef | grep find

root 20378 13964 0 11:07:20 pts/0 0:00 grep find

root 28970 1 4 11:05:46 - 0:03 find / -type f

3\. 取消 find 命令进程：

# kill 28970

4\. 查看进程：

# ps -ef | grep find

root 28972 13964 0 11:07:33 pts/0 0:00 grep find

#

要从 /etc/inittab 文件中删除该记录，可使用 rmitab 命令。例如：

# rmitab xcmd

# lsitab xcmd

#

/etc/inittab 条目的次序

/etc/inittab 文件中的基本进程条目次序安装如下：

1\. initdefault

2\. sysinit

3\. Powerfailure Detection (powerfail)

4\. Multiuser check (rc)

5\. /etc/firstboot (fbcheck)

6\. System Resource Controller (srcmstr)

7\. Start TCP/IP daemons (rctcpip)

8\. Start NFS daemons (rcnfs)

9\. cron

10.pb cleanup (piobe)

11.getty for the console (cons)

系统资源控制器 (SRC)必须在 /etc/inittab 文件的开头附近就被启动，因为启动其他的进程需要SRC进程（Daemon）。

由于NFS需要TCP/IP进程（Daemon）才能正常运行，所以TCP/IP进程必须在NFS进程之前被启动。

/etc/inittab 文件中的条目按相互依赖性排序，就是说，如果一个进程（process2）需要另外一个进程（process1）存在才能正常运行，那么在 /etc/inittab文件中，process1的条目应该在process2的条目之前。

condig log

1\.       配置登录日志

#vi /etc/syslog.conf

添加或修改

auth.info\t\t/var/adm/authlog

*.info;auth.none\t\t/var/adm/syslog\n&quot;

执行命令：

#touch /var/adm/authlog /var/adm/syslog  chown root:system /var/adm/authlog

#chmod 600 /var/adm/authlog

#chmod 640 /var/adm/syslog

#stopsrc -s syslogd

#startsrc -s syslogd

2\.      配置事件日志

#vi /etc/syslog.conf，

添加或修改

*.err;kern.debug;daemon.notice;        /var/adm/messages

#stopsrc -s syslogd

#startsrc -s syslogd

3\.      配置cron日志

#vi /etc/cronlog.conf

编辑或添加如下内容：

    logfile=/var/adm/cron/log

    size=2m

    rotate=4

    archive=/var/adm/cron

    compress

说明：本加固项仅对AIX 5300-04或更高版本有效

4\.      配置远程日志服务器（可选）

修改配置文件vi /etc/syslog.conf，

加上这几行：

auth.info\t\t@loghost

*.info;auth.none\t\t@loghost

*.emerg\t\t@loghost

local7.*\t\t@loghost

可以将此处loghost替换为实际的IP或域名。

重新启动syslog服务，依次执行下列命令：

#stopsrc -s syslogd

#startsrc -s syslogd

说明： *.*和@之间为一个Tab

5\.      启用内核级审核

#audit on

#mkitab -i cron &quot;audit:2:once:/usr/sbin/audit start 2&gt;&amp;1  &gt; /dev/console&quot;

#telinit q

#echo &quot;audit shutdown&quot; &gt;&gt; /usr/sbin/shutdown

6\.      禁止ICMP重定向，采用静态路由

以ascii方式上传如下脚本至AIX主机，并将其放入/etc/目录下：

#chmod +x /etc/rc.net-tune

#mkitab -i rctcpip &quot;rcnettune:2:wait:/etc/rc.net-tune &gt;  /dev/console 2&gt;&amp;1&quot;

rlogin

远程用户启动rlogin访问你的本地主机，此时做如下安全性检查：

1\. 本地rlogind在本地/etc/passwd文件中寻找远程用户名，没有则拒绝访问

2\. /etc/passwd中存在远程用户名，rlogind在/etc/hosts.equiv寻找远程主机名，找到则允许访问。

3\. /etc/hosts.equiv无远程主机名，rlogind在$HOME/.rhosts寻找远程主机名，找到且该项后无用户名则允许访问，找到且该项后有用户名，若远程用户名位于其中，则允许访问。注意这里的$HOME是与远程用户同名的本机用户的主目录。

4\. 若通过了/etc/passwd的检查，但没有通过/etc/hosts.equiv或者$HOME/.rhosts的检查，远程用户给出口令可以登录本机，但无法使用rcp、rsh等。反之则可以使用rcp或者rsh。

5\. /etc/hosts.equiv中的+意味着任意主机，此时与/etc/hosts无关。netterm下rlogin除root外的所有用户可以成功，solaris下简单的rlogin hostname同netterm，但是rlogin -l username hostname不成功。这个事实说明netterm下rlogin的时候，指定的参数实际上是远程主机的当前用户名。还说明hosts.equiv文件不支持rlogin -l username hostname，不支持root的rlogin。

值得注意的是两个+号出现在$HOME/.rhosts中是非常危险的，意味着任意主机任意用户都可以不用口令登录到你的用户上来。.rhosts中的第一个+意味着所有主机，与/etc/hosts文件无关。.rhosts中的第二个+意味着所有用户，与/etc/passwd文件无关。若只有一个+，netterm中的rlogin可以成功，但来自sco root下的rlogin -l jhli hostname不成功，来自sco jhli的rlogin -l jhli hostname和rlogin hostname都成功。说明当.rhosts文件中只有主机名时，不支持rlogin -l username hostname，这点和/etc/hosts.equiv一样。若+ root，则netterm因无法实现rlogin -l username hostname而失败(只能实现rlogin hostname)，来自sco root下的rlogin -l jhli hostname成功。+ +则都成功。注意，$HOME/.rhosts支持root的rlogin。

当这两个文件中没有使用+号代表所有主机时，与/etc/hosts文件有关。这两个文件中指定的hostname必须是/etc/hosts文件中出现的，而且必须是主机名，IP地址和别名无效。在/etc/hosts文件中别名位于第三列。做主机判断时与在远程主机上hostname命令所显示的东西无关，与远程主机上的/etc/hosts定义无关。如果出现与这里讲述不符合的，是因为缓冲没有得到刷新的缘故，可以通过ping相关名字得到检验。此外，若没有使用+号，rlogin localhost、rlogin 127.0.0.1的效果和rlogin 134.*.*.*、rlogin zhuzhou的效果不一样，前者的检查不会通过。当hosts.equiv中定义为localhost时，效果则反过来。

6\. rlogin -l username hostname和rlogin hostname的检查有点细微的差别，首先在/etc/passwd的检查中是以-l的参数为准的，没有-l参数才使用远程主机的当前用户名，所谓当前用户名是考虑了su出来的用户。其次，$HOME也是先以-l参数为准。第三，$HOME/.rhosts文件中的用户名不是针对-l参数来的，而是针对远程主机的当前用户名来的，但是对于这个远程主机的当前用户名，并不要求出现在/etc/passwd文件中。这第6条尤其重要，许多不成功的$HOME /.rhost就是因为对第6条的不了解。

7\. $HOME/.rhosts文件的权限问题，chmod 0都没有影响，不过当时是处理root用户。对于一般用户，一定要保证.rhosts文件对于$HOME的属主是可读的。一般来说，这个文件最好 chmod 400。对于root，如果不希望某个用户建立自己的.rhosts或者想替该用户建立.rhosts后不允许该用户自己修改，可以通过chown root .rhosts然后chmod 444 .rhosts实现。除了root，如果$HOME/.rhosts文件的属主和$HOME的属主不一致，检查将失败。

8\. $HOME/.rhosts文件中每行只跟一个用户名，若想多个指定，只好分多行指定用户名。

9\. sco unix下$HOME/.rhosts中若用+代表主机，与其他Unix系统不同，这里的+没有任何特殊的意义，所以检查将失败。但是用户名仍然可以用+代表。并且sco unix下若root的.rhosts文件go+w，则检查失败。

10\. 建议man rhosts看看，各个系统有许多细微的差别。

link

【2013AIX高手挑战赛精品辅导资料汇总】--AIX系统管理 ： [http://www.aixchina.net/club/thread-94311-1-1.html](http://www.aixchina.net/club/thread-94311-1-1.html)

AIX系统管理分类进阶考试： [http://www.aixchina.net/home/cp.php?ac=examine&amp;step=start&amp;xid=93](http://www.aixchina.net/home/cp.php?ac=examine&step=start&xid=93)

【2013AIX高手挑战赛精品辅导资料汇总】--AIX高可用： [http://www.aixchina.net/club/thread-94313-1-1.html](http://www.aixchina.net/club/thread-94313-1-1.html)

AIX高可用分类进阶考试： [http://www.aixchina.net/home/cp.php?ac=examine&amp;step=start&amp;xid=89](http://www.aixchina.net/home/cp.php?ac=examine&step=start&xid=89)

【2013AIX高手挑战赛精品辅导资料汇总】--虚拟化与云计算： [http://www.aixchina.net/club/thread-94315-1-1.html](http://www.aixchina.net/club/thread-94315-1-1.html)

虚拟化与云计算分类进阶考试： [http://www.aixchina.net/home/cp.php?ac=examine&amp;step=start&amp;xid=91](http://www.aixchina.net/home/cp.php?ac=examine&step=start&xid=91)

【2013AIX高手挑战赛精品辅导资料汇总】--AIX编程与开发： [http://www.aixchina.net/club/thread-94319-1-1.html](http://www.aixchina.net/club/thread-94319-1-1.html)

AIX编程与开发分类进阶考试： [http://www.aixchina.net/home/cp.php?ac=examine&amp;step=start&amp;xid=87](http://www.aixchina.net/home/cp.php?ac=examine&step=start&xid=87)

【2013AIX高手挑战赛精品辅导资料汇总】--存储及PowerLinux ： [http://www.aixchina.net/club/thread-94321-1-1.html](http://www.aixchina.net/club/thread-94321-1-1.html)

PowerLinux大分类进阶考试： [http://www.aixchina.net/home/cp.php?ac=examine&amp;step=start&amp;xid=85](http://www.aixchina.net/home/cp.php?ac=examine&step=start&xid=85)

与AIX高手挑战赛更多相关的内容，可以访问大赛专题： [http://www.aixchina.net/contest/2013/index.php?action=home](http://www.aixchina.net/contest/2013/index.php?action=home)

LVM

lslv

lsvg

extendlv

SRC

系统资源控制器（System Resource Controller，SRC）

http://czmmiao.iteye.com/blog/1638833

**相关文件**

| **/etc/objrepos/SRCsubsys** | 指定 SRC 子系统配置对象类。 |
| --- | --- |
| **/etc/objrepos/SRCsubsvr** | 指定 SRC 子服务器配置对象类。 |
| **/etc/services** | 定义用于因特网服务的套接字和协议。 |
| **/dev/SRC** | 指定 **AF_UNIX** 套接字文件。 |
| **/dev/.SRC-unix** | 指定临时套接字文件位置。 |

**查看SRC服务**$ps -ef|grep srcmstr    frp 618582 931544  0 15:00:09 pts/3 0:00 grep srcmstr   root  58126      1  0  Jun 01     - 0:13 /usr/sbin/srcmstr$grep srcmstr /etc/inittabsrcmstr:23456789:respawn:/usr/sbin/srcmstr # System Resource Controller

**查看ODM库中子服务信息** $odmget SRCsubsvr

**查看ODM库中子系统定义** $odmget SRCsubsys |more

lssrc

       -t Type

            Requests that a subsystem send the current status of a subserver. The command is unsuccessful if the

            subserver Type variable is not contained in the subserver object class.

startsrc

startsrc 命令

用途

启动子系统、子系统组或子服务器。

语法

启动子系统

startsrc [ Argument] -g Group}

启动子服务器

startsrc [ -h Host] -t Type [ -o Object] [ -p SubsystemPID]

描述

startsrc 命令向系统资源控制器（System Resource Controller, SRC）发送请求以启动子系统或子系统组，或向启动子服务器的子系统发送一个信息包。

如果启动子服务器的请求发送到 SRC，且该子服务器所属的子系统当前不活动，则 SRC 会启动子系统，并把启动子服务器的请求发送给子系统。

标志

-a Argument 指定子系统执行时传递给子系统的自变量字符串。该字符串从命令行发送，并附加在子系统对象类中的命令行变量上。指定的 Argument 字符串最大长度为 1200 个字符，否则命令就会失败。根据与 shell 使用的相同的规则，该命令参数由 SRC 传递到子系统。引号括起的字符串作为单个参数传递，并且以引号括起的字符串外的空格定界一个参数。 可使用单引号和双引号。

-e Environment 当子系统执行时，指定一个放入子系统环境中的环境字符串。指定的 Environment 字符串的最大长度为 1200 个字符，否则命令将失败。使用与 shell 所使用的相同的规则，SRC 为子系统设置环境。

引号括起的字符串指定给一个单一的环境变量，并且引号括起的字符串外的空格定界了每个要设置的环境变量。例如：-e &quot;HOME=/tmp TERM=dumb MESSAGE=\&quot;Multiple word message\&quot;&quot; 把 HOME=/tmp 设置为子系统第一个环境变量，把 TERM=dumb 设置为子系统第二个环境变量，把 MESSAGE=&quot;Multiple word message&quot; 设置为子系统第三个环境变量。

-g Group 指定一组要启动的子系统。如果 Group 名称未包含在子系统对象类中，命令将失败。

-h Host 指定在其上请求此启动操作的外部主机。本地用户必须作为&quot;root 用户&quot;运行。远程系统必须配置为可接受远程系统资源控制器的请求。即，srcmstr 守护进程（请参阅 /etc/inittab）必须以 -r 标志启动，并且 /etc/hosts.equiv 或 .rhosts 文件必须配置为允许远程请求。

-o Object 指定子服务器对象作为字符串传递给子系统。确定 Object 字符串的有效性是子系统的责任。

-p SubsystemPID 指定启动子服务器请求要发送到的子系统的特定实例。

-s Subsystem 指定要启动的子系统。Subsystem 可以是实际的子系统名，或子系统的同义词名称。如果子系统对象类中未包含 Subsystem，命令将失败。

-t Type 指定要启动的子服务器。如果子服务器对象类中未包含 Type，命令将失败。

示例

要使用参数和环境变量启动一个子系统，请输入：

startsrc  -s srctest  -a &quot;-D DEBUG&quot;  -e &quot;TERM=dumb HOME=/tmp&quot;

这将使用其环境中的 &quot;TERM=dumb&quot; 、&quot;HOME=/tmp&quot;并且把 &quot;-D DEBUG&quot; 作为该子系统的两个参数来启动 srctest 子系统。

要启动外部主机上的子系统组，请输入：

startsrc  -g tcpip  -h zork

这将启动 zork 机器上 tcpip 子系统组中所有的子系统。

要启动一个子服务器，请输入：

startsrc  -t tester

这将向拥有 tester 子系统的子系统发送启动子服务器的请求。

要使用命令参数启动一个子系统，请输入：

startsrc  -s srctest  -a &quot;-a 123 -b \&quot;4 5 6\&quot;&quot;

这将使 &quot;-a&quot; 作为 srctest 子系统的第一个参数，&quot;123&quot; 作为第二个参数，&quot;-b&quot; 作为第三个参数，而 &quot;456&quot; 作为第四个参数。

文件

/etc/objrepos/SRCsubsys 指定 SRC 子系统配置对象类。

/etc/objrepos/SRCsubsvr 指定 SRC 子服务器配置对象类。

/etc/services 定义因特网服务所用的套接字和协议。

/dev/SRC 指定 AF_UNIX 套接字文件。

/dev/.SRC-unix 指定临时套接字文件的位置。

stopsrc

stopsrc 命令

用途

停止子系统、子系统组或子服务器。

语法

停止子系统

stopsrc [ -h Host] [ -f | -c] { -a | -g Group | -p SubsystemPID | -s Subsystem }

停止子服务器

stopsrc [ -h Host] [ -f] -t Type [ -p SubsystemPID] [ -P SubserverPID | -o Object]

描述

stopsrc 命令向系统资源控制器（SRC）发送要求停止一个子系统、一组子系统或所有子系统的请求。stopsrc 命令向系统资源控制器发送子系统请求包，该请求包转发至子系统用于停止子服务器的请求。

如果没有 -f（强制停止）标志, 则假设为正常的停止操作。正常停止要求子系统或子服务器完成所有当前处理，在所有应用程序活动完成时释放资源，然后结束。子系统不再接受任何新的工作请求。

强制停止要求子系统或子服务器迅速结束，释放所有资源，但不等待应用程序活动完成。

取消操作是在子系统的资源释放后以及一段宽延时间后才停止子系统。此宽延时间在子系统的对象类中指定。取消停止只用于子系统的停止，并且总是以 SIGTERM 信号发送给子系统。子系统抓取这个信号，执行子系统清除操作，然后结束。如果子系统没有在等待时间内结束（等待时间在子系统对象类中指定），则将 SIGKILL 信号发送给子系统以确保子系统的停止。

如果子系统使用套接字或消息队列进行通信，则构造一个数据包并发送给子系统。如果子系统使用信号进行通信，则将子系统对象类中的适当的信号发送给子系统。

标志

-a 指定停止所有子系统。

-c 指定停止请求是已取消的停止请求。对于取消停止请求，将 SIGTERM 信号发送至子系统。在子系统对象类中指定的等待时间过去后，如果子系统仍未停止，则将 SIGKILL 信号发送至子系统。

-f 指定强制停止请求。

-g Group 指定停止一组子服务器。如果 Group 名称未包含在子系统对象类中，该命令将失败。

-h Host 指定请求该停止操作的外部 Host 机器。本地用户必须以&quot;root 用户&quot;身份运行。必须将远程系统配置为可接受远程系统资源控制器的请求。即 srcmstr 守护进程（请参阅 /etc/inittab）必须以 -r 标志启动，并且 /etc/hosts.equiv 或 .rhosts 文件必须配置为允许远程请求。

-o Object 指定子服务器 Object 值是作为字符串发送给子系统的。

-p SubsystemPID 指定要停止的子系统的特定实例，或子服务器（停止子服务器请求要传递到该子系统）的特定实例。

-P SubserverPID 指定子服务器 PID 是作为字符串传递给子系统的。

-s Subsystem 指定要停止的子系统。Subsystem 参数可以是实际的子系统名称或子系统的同义词名称。 stopsrc 命令停止所有当前活动的子系统实例。如果子系统对象类中未包含 Subsystem 名称，该命令将失败。

-t Type 指定要停止的子服务器。如果子服务器对象类中未包含指定的 Type，stopsrc 命令将失败。

示例

要在外部主机上强制停止一个子系统，请输入：

stopsrc -h zork -s srctest -f

这将强制停止 zork 机器上的 srctest 子系统的所有实例。

要取消停止一个子系统组，请输入：

stopsrc -g tcpip -c

这将在 tcpip 组的所有子系统上激活停止取消。

要停止一个子服务器，请输入:

stopsrc -t tester -p 1234

这将停止 tester 子服务器，它属于子系统 PID 为 1234 的 srctest 子系统。

要停止所有子系统，请输入：

stopsrc -a

这将停止本地机器上所有活动的子系统。

文件

/etc/objrepos/SRCsubsys 指定 SRC 子系统配置对象类。

/etc/objrepos/SRCsubsvr 指定 SRC 子服务器配置对象类。

/etc/services 定义因特网服务使用的套接字和协议。

/dev/SRC 指定 AF_UNIX 套接字文件。

/dev/.SRC-unix 指定临时套接字文件的位置。

refresh

**refresh**

**用途**

请求子系统或子系统组的刷新。**描述**refresh 命令发送一个转发到该子系统的子系统刷新请求给系统资源控制器。刷新操作依赖于子系统。注意：如果子系统的通信方法是信号，refresh命令失败。

example

查看ssh服务状态# lssrc -s sshdSubsystem         Group            PID                      Status sshd                    ssh                3866742          active停止和启动 ssh 服务# stopsrc -s sshd# startsrc -s sshd

#lssec-f ftp

src

SRC 即子系统控制器。拥有一个或多个守护进程的子系统程序员可使用 SRC 服务为它们的应用程序定义一个一致的系统管理接口。SRC 提供一组单独的命令以启动、停止、跟踪、刷新以及查询子系统的状态。

此外，SRC 提供的通知设施错误。可使用此设施合并系统特定的恢复方法。包括的恢复信息的类型仅受某一需求的限制，该需求即通知方法在文件中为字符串，并且可被执行。

SRC 对象

SRC 通信类型

对使用 SRC 的子系统进行编程

给 SRC 定义子系统

其它 SRC 子例程列表

与 SRC 交互的子系统

SRC 将子系统定义为旨在作为一个单元执行相关函数的一个程序或一组相关程序。请参阅《AIX 5L V5.3 系统管理指南：操作系统与设备》 中的&quot;系统资源控制器概述&quot;，以获得有关子系统特征的更为详细的描述。

子服务器即属于子系统的进程，它受管于子系统。

SRC 在 SRC 对象类中的对象上运作。将子系统定义为 SRC 的子系统对象；将子服务器定义为子服务器类型对象。在 usr/include/sys/srcobj.h 文件中，对与每种类型的对象相关联的结构进行预定义。

SRC 可对子系统、子服务器和子系统组级别的对象发出 SRC 命令。子系统是一组任意用户指定的子系统。对子系统进行分组允许仅调用一个单独命令便可控制多个子系统。子系统的各个组还可以共享公共通知方法。

SRC 通过发送信号并交换请求和答复包与子系统通信。除了信号之外，SRC 还辨认套接字和 IPC 消息队列通信类型。可把许多子例程用作 SRC API 以辅助子系统和 SRC 之间的编程通信。SRC API 还支持客户机程序和 SRC 之间的编程通信。有关可用子例程的更多信息，请参阅其它 SRC 子例程列表。

SRC 和 init 命令

SRC 在运营上独立于 init 命令。然而，SRC 致力于扩展此命令提供的进程衍生功能。除了提供单一控制点以启动、停止、跟踪、刷新和查询子系统状态外，SRC 还可控制个别子系统的操作、支持远程系统控制并记录子系统故障。

在运营上，init 命令和 SRC 交互仅发生在 srcmstr（SRC 主）守护进程被嵌入到 inittab 文件中时。在缺省情况下，srcmstr 守护进程位于 inittab 文件中。在此情况下，init 命令在系统启动时启动 srcmstr 守护进程，和其它进程一样。必须具有 root 用户权限或在系统组中才可调用 srcmstr 守护进程。

编辑将要与 srcmstr 守护进程交互的程序

要使程序与 srcmstr 守护进程交互，必须包括 /usr/include/spc.h 文件，而且应该使用 libsrc.a 库编译程序。如果子系统使用信号与 SRC 通信，则不需要此支持。

SRC 操作

要使用 SRC 功能，必须使用两种方法将子系统与 srcmstr 守护进程交互：

必须为 SRC 子系统对象类中的子系统创建子系统对象。

如果子系统使用信号，则它不必使用 SRC 子例程。然而，如果它使用消息队列或套接字，它必须使用 SRC 子例程响应停止请求。

所有的 SRC 子系统必须支持 stopsrc 命令。SRC 使用此命令停止带有 SIGNORM（正常停止）、SIGFORCE（强行停止）或 SIGCANCEL（取消系统）信号的子系统及其子服务器。

对于 startsrc、lssrc -l、traceson、tracesoff 和 refresh 命令，长状态和子服务器状态报表以及 SRC 通知机制，子系统支持是可选的。请参阅对使用 SRC 的子系统进行编程，以获得详细信息。

SRC 能力

SRC 为子系统程序员提供以下支持：

支持向子系统开始、停止发送请求的常用命令接口

子系统和子系统组的中心控制点

向子系统发送请求的常用该格式

子服务器的定义，由于定义给子系统的子服务器是唯一的，这样可以管理每个子服务器

定义子系统特定错误通知方法的能力

将系统特定响应定义给状态、跟踪支持和配置刷新请求的能力

在网络计算环境中服务于子系统请求的单点控制

SRC 对象

系统资源控制器（SRC）定义并管理三个对象类：

子系统对象类

子服务器类型对象类

通知对象类

同时，这些对象类还代表 SRC 在其中执行其函数的域。一组预定义的对象类描述符由 SRC 支持的子系统配置的可能集合组成。

注意：仅需要 SRC 子系统对象类。子服务器类型和通知对象类的使用是系统相关的。

子系统对象类

子系统对象类包含所有 SRC 子系统的描述符。在子系统可被 SRC 辨认之前，必须在这个类中配置该子系统。

子系统对象类的描述符是在 /usr/include/sys/srcobj.h 文件的 SRCsubsys 结构中定义的。子系统对象描述符和描述符表提供了系统描述符以及与每个描述符相关的 mkssys 和 chssys 命令标志的简短演示。

表 9\. 子系统对象描述符和缺省值 描述符 缺省值 标志

子系统名称

-s

子系统命令路径

-p

命令参数

-a

执行优先级 20 -E

多个实例 NO -Q -q

用户标识

-u

同义词名称（关键字）

-t

启动操作 ONCE -O -R

stdin /dev/console -i

stdout /dev/console -o

stderr /dev/console -e

通信类型 Socket -K -I -S

子系统消息类型

-m

通信 IPC 队列密钥

-l

组名

-G

SIGNORM 信号

-n

SIGFORCE 信号

-f

显示 是 -D -d

等待时间 20 秒 -w

Auditid

子系统对象描述符定义如下：

子系统名称 指定子系统对象的名称。这个名称不得超过 30 个字节，其中包括 null 终止符（对于单字节字符集为 29 个字符，而对于多字节字符集为 14 个字符）。此描述符必须符合 POSIX。此字段是必需的。

子系统命令路径 指定由子系统启动命令执行的程序的全路径名。路径名不得超过 200 个字节，其中包括 null 终止符（对于单字节字符集为 199 个字符，而对于多字节字符集为 99 个字符）。路径名必须符合 POSIX。此字段是必需的。

命令参数 指定必须传送到启动子系统的命令的任何参数。参数不得超过 200 个字节，其中包括 null 终止符（对于单字节字符集为 199 个字符，而对于多字节字符集为 99 个字符）。参数是由 srcmstr 守护进程根据 shell 使用的相同规则解析的。例如：引用字符串作为单独的参数传递，引用字符串外的空格是定界参数。

执行优先级 指定要运行的子系统的进程优先级。由 srcmstr 守护进程启动的子系统运行此优先级。缺省值为 20。

多个实例 指定一次可以运行的子系统实例数。值 NO（-Q 标志）指定一次仅可运行一个子系统实例。在该子系统已在运行时试图启动它的这一操作将失败，试图在同一 IPC 消息队列密钥上启动某一子系统也将失败。值 YES（-q 标志）指定多个子系统可使用同一 IPC 消息队列，并且同一子系统可有多个实例。缺省值为 NO。

用户标识 指定在其下运行子系统的用户标识。值 0 指示 root 用户。此字段是必需的。

同义词名称 指定将要用作子系统备用名的字符串。这个字符串不得超过 30 个字节，其中包括 null 终止符（对于单字节字符集为 29 个字符，而对于多字节字符集为 14 个字符）。此字段是可选的。

启动操作 指定 srcmstr 守护进程是否在子系统异常终止后重新启动它。值 RESPAWN（-R 标志）指定 srcmstr 守护进程应该重新启动子系统。值 ONCE（ -O 标志）指定 srcmstr 守护进程不应该试图重新启动发生故障的系统。在指定的等待时间内，对两次重新启动有衍生限制。如果不能成功地重新启动发生故障的子系统，请参考通知方法选项。缺省值为 ONCE。

标准输入文件／设备 指定子系统从其检索其输入的文件或设备。缺省值为 /dev/console。此字段不得超过 200 个字节，其中包括 null 终止符（对于单字节字符集为 199 个字符，而对于多字节字符集为 99 个字符）。如果通信类型为套接字，则忽略此字段。

标准输出文件／设备 指定要向其发送其输出的文件或设备。此字段不得超过 200 个字节，其中包括 null 终止符（对于单字节字符集为 199 个字符，而对于多字节字符集为 99 个字符）。缺省值为 /dev/console。

标准错误文件／设备 指定子系统将要向其写入其错误消息的文件或设备。此字段不得超过 200 个字节，其中包括 null 终止符（对于单字节字符集为 199 个字符，而对于多字节字符集为 99 个字符）。将故障作为通知方法的一部分处理。缺省值为 /dev/console。

注意：将灾难性错误被发送到错误日志。

通信类型 指定 srcmstr 守护进程和子系统之间的通信方法。可定义三种类型：IPC（-I）、套接字（-K）或信号（-S）。缺省值为套接字。

通信 IPC 队列密钥 指定与 srcmstr 守护进程用来与子系统通信的 IPC 消息队列密钥相对应的十进制值。对于使用 IPC 消息队列进行通信的子系统，此字段是必需的。使用具有全限定路径名和标识参数的 ftok 子例程，以确保此密钥唯一。srcmstr 守护进程在启动子系统之前创建消息队列。

组名 指定子系统为组的成员。此字段不得超过 30 个字节，其中包括 null 终止符（对于单字节字符集为 29 个字符，而对于多字节字符集为 14 个字符）。此字段是可选的。

子系统消息类型 指定置于子系统消息队列上的消息的 mtype。子系统通过使用 msgrcv 或 msgxrcv 子例程使用该值检索消息。如果正在使用消息队列，则需要此字段。

SIGNORM 信号值 指定发出正常停止请求时将要发送给子系统的值。对于使用信号通信类型的子系统，此字段是必需的。

SIGFORCE 信号值 指定发出强制停止请求时将要发送给子系统的值。对于使用信号通信类型的子系统，此字段是必需的。

显示值 指示是否可将不可操作的子系统的状态显示在 lssrc -a 或 lssrc -g 输出上。-d 标志指示显示；-D 标志指示不显示。缺省值为 -d（显示）。

等待时间 指定在采取备用操作之前子系统完成重新启动或停止请求所需的时间（以秒为单位）。缺省值为 20 秒。

Auditid 指定子系统审计标识。定义子系统时由 srcmstr 守护进程自动创建的，此字段为安全系统所用（如果配置）。此字段无法被程序设置或更改。

请参阅给 SRC 定义子系统，以获得定义和修改子系统对象的相关信息。

子服务器类型对象类

如果子系统具有子服务器并且该子系统希望从 srcmstr 守护进程处接收到子服务器相关命令，则必须在此类中配置对象。

此对象类包含三个描述符，这些描述符被定义在 srcobj.h 文件的 SRCsubsvr 结构中：

子服务器标识（密钥） 指定子服务器类型对象标识的名称。子服务器类型名称集定义了子服务器命令 -t 标志的允许值。名称长度不得超过 30 个字节，其中包括 null 终止符（对于单字节字符集为 29 个字符，而对于多字节字符集为 14 个字符）。

所有子系统名称 指定拥有子服务器对象的子系统的名称。将此字段作为链接定义给 SRC 子系统对象类。

代码点 指定标识子服务器的十进制数字。将代码点传递到在 SRC 请求结构的 subreq 结构的 object 字段中控制子服务器的子系统。如果在命令中也提供了子服务器对象名，则 srcmstr 守护进程将代码点转发到 subreq 结构的 objname 字段中的子系统。请参阅 spc.h 文件文档中的&quot;SRC 请求结构示例&quot;，以获得这些因素的示例。

参考子服务器的命令将每个子服务器标识为子服务器的命名类型，并且还可将某一名称追加到子服务器类型的每个实例。SRC 守护进程使用子服务器类型确定子服务器的控制子系统，但不检查子服务器名称。

请参阅给 SRC 定义子系统，以获得定义和修改子服务器类型对象的相关信息。

通知对象类

这个类为 srcmstr 守护进程提供了一个机制，使其在检测到子系统故障时调用子系统提供的例程。当 SRC 守护进程接收到指示子系统进程终止的 SIGCHLD 信号，它就检查子系统（由 srcmstr 守护进程维护的）的状态以确定这一终止是否由 stopsrc 命令引发。如果未发出 stopsrc 命令，则此终止将被解释为异常终止。如果定义中的重新启动操作不指定重新衍生，或重新衍生尝试失败，则 srcmstr 守护进程尝试着从通知对象类读取与子系统名称相关的对象。如果找到类似对象，则运行与子系统相关联的方法。

如果没有在通知对象类中找到子系统对象，则 srcmstr 守护进程就确定该子系统是否属于某一组。如果是，srcmstr 守护进程尝试着从通知对象类读取该组名的对象。如果找到类似对象，则调用与之相关的方法。这样，子系统的组便可共享常用方法。

注意：子系统通知方法优先于组通知方法。因此，子系统可属于一起启动的某一组，但仍然定义特定的恢复或清除例程。

通知对象由两个描述符定义：

子系统名称或组名 指定为其定义通知方法的子系统或组的名称。

通知方法 指定当 srcmstr 守护进程检测到子系统或组的异常终止时执行的例程的全路径名。

当特定恢复或清除工作需要在重新启动子系统之前被执行时，此类通知很有用处。它还可被用来收集信息以确定子系统异常停止的原因。

通知对象是通过使用 mknotify 命令创建的。要修改通知对象，必须使用 rmnotify 命令除去现有通知对象，然后创建新的通知对象。

mknotify 向 SRC 配置数据库添加通知方法

rmnotify 从 SRC 配置数据库除去通知方法

srcmstr 守护进程记录子系统恢复活动。该子系统复杂报告子系统故障。

SRC 通信类型

系统资源控制器（SRC）支持三种通信类型：信号、socket 和进程间通信（IPC）消息队列。选择的通信类型决定子系统利用 SRC 功能的等级。

注:

所有的子系统，不管其在系统环境对象中指定的通信类型如何，都必须能支持受限的信号通信。必须定义信号捕捉器，以处理 SIGTERM（取消停止）信号。SIGTERM 信号指示子系统应该清除所有的资源然后终止。

请参阅以下章节了解更多关于 SRC 通信类型的信息：

信号通信

Socket 通信

IPC 消息队列通信

srcmstr 守护程序和子系统之间的通信表概括了与 SRC 关联的通信类型操作。

srcmstr 守护程序与子例程之间的通信

功能 使用 IPC 或 Socket 使用信号

启动

子系统 SRC 派生和执行以创建子系统进程。 SRC 派生和执行以创建子系统进程。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

正常停止

子系统 使用 IPC 消息队列或套接字发送请求至子系统。 发送 SIGNORM 至子系统。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

强制停止

子系统 使用 IPC 消息队列或套接字发送请求至子系统。 发送 SIGFORCE 至子系统。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

取消停止

子系统 发送 SIGTERM，然后发送 SIGKILL 至子系统的进程组。 发送 SIGTERM，然后发送 SIGKILL 至子系统的进程组。

短暂停止

子系统 由 SRC 实现（无子系统请求）。 由 SRC 实现（无子系统请求）。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

长时间停止

子系统 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

跟踪打开／跟踪关闭

子系统 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

刷新

子系统 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

子服务器 使用 IPC 消息队列或套接字发送请求至子系统。 不受支持。

通知

子系统 由子系统提供的方法实现。 由子系统提供的方法实现。

信号通信

子系统和 srcmstr 守护进程之间最基本的通信类型由信号实现。因为信号构成单向通信方案，信号子系统识别的唯一 SRC 命令是停止请求。使用信号的子系统不识别长状态、刷新或跟踪请求。它们也不识别子服务器。

信号子系统必须实现信号捕捉器例程，例如 sigaction、sigvec 或 signal 子例程，以处理 SIGNORM 和 SIGFORCE 请求。

通过发出 mkssys -Snf 命令字符串或使用 defssys 和 addssys 子例程，在 SRC 子系统对象类中指定信号子系统。

addssys 向 SRC 配置数据库添加子系统定义

defssys 使用缺省值初始化新的子系统定义

mkssys 向 SRC 配置数据库添加子系统定义

Socket 通信

越来越多的子系统程序员选择的通信选项为 socket。Socket 也是 srcmstr 守护进程的缺省通信类型。请参阅在 AIX 5L Version 5.3 Communications Programming Concepts 中的 Socket 概述以获取更多信息。

srcmstr 守护进程使用 socket 接收命令进程的工作请求。当选择了这种通信类型时，srcmstr 守护进程创建子系统套接字，子系统将在其中接收 srcmstr 守护进程请求。UNIX 套接字（AF_UNIX）为本地子系统创建。因特网套接字（AF_INET）为远程子系统创建。以下步骤描述命令处理顺序：

命令进程接受来自输入设备的命令，构造工作请求消息，然后将工作请求 UDP 数据报发送到明确的SRC 端口上的 srcmstr 守护进程。AF_INET 在 /etc/services 文件中定义。

srcmstr 守护进程侦听明确的 SRC 端口的工作请求。当接收到工作请求时。它会告诉系统填充socket 子例程的 sockaddr 结构，以获取原系统的地址，并将地址和端口号追加到工作请求。

srcmstr 守护进程使用 srcrrqs 和 srcsrpy 子例程。它只处理它能处理的那些请求，然后将信息发送回命令进程。其它的请求被转发到已经为工作请求指定了子系统的端口上合适的子系统。

子系统侦听之前由 srcmstr 守护进程获取的端口上的子系统。（当 srcmstr 守护进程启动子系统时，每个子系统继承一个端口。）子系统处理工作请求并将回复发送回命令进程。

命令进程侦听指定端口上的响应。

srcmstr 守护进程使用的文件访问许可权和套接字的地址在 /dev/SRC 和 /dev/.SRC-unix 临时目录中维护。虽然使用 ls 命令可以显示这些目录中包含的信息，但这些信息只用于内部 SRC 用途。

消息队列和套接字提供同样的子系统功能。

请参阅对使用 SRC 的子系统进行编程获取更多信息。

srcrrqs 将您子系统响应的目标地址保存到接收的数据包。（另见多线程安全版本 srcrrqs_r）

srcsrpy 将子系统响应数据包发送至子系统接收的请求。

IPC 消息队列通信

IPC 消息队列功能类似于套接字功能。这两种通信类型都支持功能完全的 SRC 环境。

当通信类型为 IPC 消息队列时，srcmstr 守护进程使用套接字接收命令进程的工作请求，然后使用IPC 消息队列，子系统在其中接收 SRC 消息。当子系统启动时，创建消息队列，然后使用它。消息队列使用以下命令处理顺序与 srcmstr 守护进程进行通信：

srcmstr 守护进程从 SRC 子系统对象获取消息队列标识，然后将消息发送到子系统。

子系统等待消息队列，然后发出 msgrcv 子例程，以子系统请求要求的 subreq 结构接收来自消息队列的命令。

子系统调用 srcrrqs 子例程，以获取响应消息时使用的标记标识。

子系统继承并处理接收的命令。根据命令，子系统创建 svrreply 或 statcode 数据结构以将回复返回到命令进程。请参阅 /usr/include/spc.h 文件获取关于这些结构的更多信息。

子系统调用 srcsrpy 子例程以将回复缓存发送回命令进程。

对使用 SRC 的子系统进行编程

系统资源控制器（SRC）命令是可执行程序，它执行命令行的选项。在验证了命令语法之后，命令调用 SRC 运行时子例程以构造用户数据报协议 (UDP)数据报，并将其发送到 srcmstr 守护进程。

以下章节提供关于 SRC 子例程以及子系统如何使用它们与 SRC 主进程进行通信的更多信息。

对子系统编程以接收 SRC 请求.

对子系统编程以处理 SRC 请求数据包.

对子系统编程以发送答复数据包.

对子系统编程以返回 SRC 错误数据包.

响应跟踪请求.

响应刷新请求.

对子系统编程以接收 SRC 请求

与接收 SRC 请求关联的编程任务因为为子系统指定的通信类型不同而不同。srcmstr 守护进程使用套接字接收命令进程的工作请求，并构造必需的套接字或消息队列以转发工作请求。每个子系统需要验证其套接字或消息队列的创建。请参阅SRC 通信类型获取 SRC 通信类型的描述。请阅读以下章节获取在子系统上编程以接收 SRC 请求数据包的特定通信类型指南的相关信息。

接收 SRC 信号.

使用套接字接收 SRC 请求数据包.

使用消息队列接收 SRC 请求数据包.

注意：所有的子系统（不管其通信类型如何）必须定义信号捕捉器例程以处理 SIGTERM 请求。

接收 SRC 信号

使用信号作为其通信类型的子系统必须定义信号捕捉器例程以捕捉 SIGNORM 和 SIGFORCE 信号。使用的信号捕捉方法是依赖于子系统的。以下是可以用于该目的的子例程类型的两组示例。

sigaction、sigvec 或 signal 子例程 指定传递信号时采取的操作。

sigset、sighold、sigrelse 或 sigignore 子例程 增强信号设施并提供应用程序进程的信号管理。

请参阅信号通信获取更多信息。

使用套接字接收 SRC 请求数据包

当进行 socket 子系统编程以接收 SRC 请求数据包时，请使用以下指南：

通过指定 /usr/include/spc.h 文件将 SRC 子系统结构包括在您的子系统代码中。该文件包含子系统用来响应 SRC 命令的结构。另外，spc.h 文件包括 srcerrno.h 文件，它不需要被独立包括。

srcerrno.h 文件包含用于守护进程支持的错误代码定义。

当启动套接字子系统时，子系统接收 SRC 请求数据包所在的套接字被设置为文件描述符 0。子系统应该通过调用 getsockname 子例程（返回子系统套接字的地址），验证该值。如果文件描述符 0 不是套接字，则子系统应该记录为错误，然后退出。请参阅在AIX 5L Version 5.3 Communications Programming Concepts 中的 &quot;读取因特网数据报实例程序&quot;，以了解关于 getsockname 子例程可如何用于返回子系统套接字的地址的信息。

如果子系统轮询多个套接字，则请使用 select 子例程确定哪些套接字需要读取。请参阅在AIX 5L Version 5.3 Communications Programming Concepts 中的 &quot;检查暂挂连接实例程序&quot;，以获取关于 select 子例程如何用于此目的的更多信息。

使用 recvfrom 子例程从套接字获取请求数据包。

注意：子系统响应数据包的返回地址在接收到的 SRC 请求数据包中。此地址不应与 recvfrom 子例程返回作为其参数之一的地址混淆。

Recvfrom 子例程完成且接收到数据包之后，使用 srcrrqs 子例程返回指向静态 srchdr 结构的指针。该指针包含子系统回答的返回地址。每次调用 srcrrqs 子例程都会覆盖此结构，所以如果在下一次调用srcrrqs 子例程之后需要其内容，应该将其存储。

请参阅对子系统编程以处理 SRC 请求数据包以了解与 SRC 建立子系统通信的下一个步骤。

使用消息队列接收 SRC 请求数据包

当进行消息队列子系统编程以接收 SRC 请求数据包时，请使用以下指南：

通过指定 /usr/include/spc.h 文件将 SRC 子系统结构包括在您的子系统代码中。该文件包含子系统用来响应 SRC 命令的结构。另外，spc.h 文件包括 srcerrno.h 包含文件，它不需要被独立包括。Srcerrno.h 文件包含守护进程支持的错误代码定义。

指定 -DSRCBYQUEUE 作为一个编译选项。这将一个消息类型（mtype）字段作为 srcreq 结构中的第一个字段。该结构应该在接收到 SRC 数据包的任何时候使用。

已经启动子系统时，使用 msgget 子例程来验证在系统启动时创建了消息队列。如果没有创建消息队列，子系统应该记录错误并退出。

如果子系统轮询多个消息队列，使用 select 子例程确定哪个消息队列有需要读取的内容。请参阅在 AIX 5L Version 5.3 Communications Programming Concepts 中的 &quot;检查暂挂连接实例程序&quot;，以获取关于 select 子例程如何用于此目的的信息。

使用 msgrcv 或 msgxrcv 子例程从消息队列获取数据包。子系统响应数据包的返回地址在接收到的数据包中。

当 msgrcv 或 msgxrcv 子例程完成且已经接收到数据包之后，调用 srcrrqs 子例程来完成接收过程。Srcrrqs 子例程返回指向静态 srchdr 结构（每次调用 srcrrqs 子例程时都被覆盖）的指针。该指针包含子系统回答的返回地址。

对子系统编程以处理 SRC 请求数据包

子系统必须能够处理停止请求。可以选择子系统来支持启动、状态、跟踪和刷新请求。

处理请求数据包涉及两个步骤的过程：

读 SRC 请求数据包

编写子系统对 SRC 请求的响应

读 SRC 请求数据包

子系统以 srcreq 结构（如同 /usr/include/spc.h 文件中所定义）的形式接收 SRC 请求数据包。子系统请求位于 srcreq 结构的 subreq 结构中：

struct subreq

short object; /*object to act on*/

short action; /*action START, STOP, STATUS, TRACE,

REFRESH*/

short parm1; /*reserved for variables*/

short parm2; /*reserved for variables*/

char objname; /*object name*/

subreq 结构的 Object 字段指示请求应用于其上的对象。请求应用于子系统时，object 字段被设置为 SUBSYSTEM 常数。否则，object 字段被设置为子服务器代码点，或者 objname 字段被作为字符串设置为子服务器 PID。确定请求应用于哪个对象是子系统的责任。

Action 字段指定子系统请求的操作。子系统应该理解 START、STOP 和 STATUS 操作码。TRACE 和 REFRESH 操作码可选。

Parm1 和 parm2 字段由每个操作进行不同使用。

Action parm1 parm2

STOP NORMAL 或 FORCE

STATUS LONGSTAT 或 SHORTSTAT

TRACE LONGTRACE 或 SHORT-TRACE TRACEON 或 TRACEOFF

START 子服务器和 REFRESH 操作不使用 parm1 和 parm2 字段。

编写子系统对 SRC 请求的响应

当对 SRC 定义了子系统对象时，为大部分 SRC 请求编写了合适的子系统操作。请参阅SRC 对象和给 SRC 定义子系统以了解更多信息。子系统用于响应 SRC 请求的结构在 /usr/include/spc.h 文件中定义。子系统可能使用下列 SRC 运行时子例程以满足命令处理需求：

srcrrqs 允许子系统存储来自请求的报头。

srcsrpy 允许子系统向请求发出答复。

请参阅响应跟踪请求和响应刷新请求，以了解关于在子系统中为这些命令编写支持的信息。

状态请求处理需要任务和子例程的组合。请参阅处理 SRC 状态请求以了解更多信息。

子系统接收到它们不能处理或无效的请求时，它们必须发送错误代码为 SRC_SUBICMD 的错误数据包以响应未知的或无效的请求。SRC 将操作码 0-255 保留作 SRC 内部使用。如果您的子系统接收到包含无效操作码的请求，则子系统必须返回 SRC_SUBICMD 错误代码。 SRC 支持的有效操作码在 spc.h 文件中定义。也可以定义子系统特定的操作码。如果没有由 SRC 或您的子系统定义，操作码无效。请参阅对子系统编程以返回 SRC 错误数据包以了解更多信息。

注意：操作码 0-255 被保留给 SRC 使用。

处理 SRC 状态请求

子系统可能被请求提供三种类型的状态报告：长子系统状态、短子服务器状态和长子服务器状态。

注意：短子系统状态报表由 srcmstr 守护进程执行。这种类型报告的 Statcode 和答复状态值常量在 /usr/include/spc.h 文件中定义。&quot;状态值常量&quot;表列出需要的和建议的答复状态值代码。

答复状态值代码

值 意义 子系统 子服务器

SRCWARN 接收到停止请求。（将在 20 秒内被停止。） X X

SRCACT 启动并激活。 X X

SRCINAC 未激活。

SRCINOP 无效的。 X X

SRCLOSD 结束。

SRCLSPN 正在结束过程中。

SRCNOSTAT 空闲。

SRCOBIN 打开，但是未激活。

SRCOPND 打开。

SRCOPPN 正在打开过程中。

SRCSTAR 启动。

X

SRCSTPG 停止。 X X

SRCTST 测试激活。

SRCTSTPN 测试暂挂。

SRC lssrc 命令显示接收到的关于标准输出的信息。由子系统返回的响应长状态请求的信息由子系统进行判断。如果需要，拥有子服务器的子系统负责跟踪和报告子服务器的状态更改。使用 srcstathdr 子例程来检索标准状态报头，以传递回到至您状态数据的开始处。

处理状态请求时，建议使用下列步骤：

要从子系统（短或长）返回状态，分配一个 statcode 结构的数组加上一个 srchdr 结构。Srchdr 结构必须启动您响应状态请求而正在发送的缓冲区。Statcode 结构在 /usr/include/spc.h 文件中定义。

struct statcode

;

使用 SUBSYSTEM 常量填充 objtype 字段以指示状态用于子系统，或者使用子服务器代码点以指示状态用于子服务器。

使用 spc.h 文件中定义的 SRC 状态常量之一填充 status 字段。

使用您希望显示为状态的 NLS 文本填充 objtext 字段。此字段必须为以 NULL 终止的字符串。

使用子系统或应用 objtext 字段的子服务器的名称填充 objname 字段。此字段必须为以 NULL 终止的字符串。

注意：子系统和请求者可以协商将其它子系统定义的信息发送回请求者。请参阅srcsrpy 连续数据包以了解关于这种类型响应的更多信息。

对子系统编程以发送答复数据包

子系统返回至 SRC 的数据包应该为 /usr/include/spc.h 文件中所定义的 srcrep 的形式。srcrep 结构一部分的 svrreply 结构将包含子系统答复：

struct svrreply

;

使用 srcsrpy 子例程向请求者返回一个数据包。

创建答复

要编写子系统答复，使用下列步骤：

使用适用的 SRC 错误代码填充 rtncode 字段。使用 SRC_SUBMSG 作为 rtncode 字段来返回子系统特定的 NLS 消息。

使用 SUBSYSTEM 常量填充 objtype 字段以指示答复用于子系统，或者使用子服务器代码点以指示答复用于子服务器。

使用子系统名称、子服务器类型或应用于答复的子服务器对象填充 objname 字段。

使用子系统特定的 NLS 消息填充 rtnmsg 字段。

在 srcsrpy Continued 参数中键入合适的条目。请参阅&quot;srcsrpy 连续数据包&quot;以了解更多信息。

注意：来自子系统的最后一个数据包在 srcsrpy 子例程的 Continued 参数中始终必须指定 END。

srcsrpy 连续数据包

子系统以连续数据包的形式响应 SRC 请求。可以指定两种类型的连续数据包：参考消息和答复数据包。

参考消息不被传递回客户机。相反，它被打印到客户机的标准输出。消息必须包含 NLS 文本，消息标记由发送子系统填充。要发送这种类型的连续数据包，在 srcsrpy 子例程的 Continued 参数中指定 CONTINUED。

注意：STOP 子系统操作不允许任何种类的连续。然而，由子系统从 SRC 接收到的所有其它操作请求可能被发送一条参考消息。

答复数据包被传递回客户机以进一步处理。因此，数据包必须由子系统和请求者协商一致。这种类型连续的一个实例为状态请求。响应子系统状态请求时，在 srcsrpy Continued 参数中指定 STATCONTINUED。状态报告完成时，或者已经发送所有子系统定义的答复数据包时，在 srcsrpy Continued 参数中指定 END。然后，数据包被传递到客户机，以指示答复结束。

对子系统编程以返回 SRC 错误数据包

需要子系统同时为 SRC 错误和非 SRC 错误返回错误数据包。

返回 SRC 错误时，子系统返回的答复数据包应该以 srcrep 结构的 svrreply 结构形式，objname 字段填充子系统名称、子服务器类型或错误的子服务器对象。如果与 SRC 错误关联的 NLS 消息不包含任何标记，错误数据包以短形式返回。这意味着错误数据包只包含 SRC 错误号。然而，如果标记与错误相关联，则应该返回来自消息目录的标准 NLS 消息文本。

返回非 SRC 错误时，答复数据包应该为 svrreply 结构，rtncode 字段设置为 SRC_SUBMSG 常量，rtnmsg 字段设置为子系统特定的 NLS 消息。Rtnmsg 字段被打印到客户机的标准输出。

响应跟踪请求

支持 traceson 和 tracesoff 命令取决于子系统。如果您选择支持这些命令，可以为子系统和子服务器指定跟踪操作。

子系统跟踪请求将以下列形式到达：子系统跟踪请求将 subreq action 字段设置为 TRACE 常量，将 subreq object 字段设置为 SUBSYSTEM 常量。跟踪操作使用 parm1 来指示 LONGTRACE 或 SHORTTRACE 跟踪，使用 parm2 来指示 TRACEON 或 TRACEOFF。

当子系统接收到 parm1 设置为 SHORTTRACE 且 parm2 设置为 TRACEON 的跟踪子系统数据包时，子系统应该打开短跟踪。相反，当子系统接收到 parm1 设置为 LONGTRACE 且 parm2 设置为 TRACEON 的跟踪子系统数据包时，子系统应该打开长跟踪。当子系统接收到 parm2 设置为 TRACEOFF 的跟踪子系统数据包时，子系统应该关闭子系统跟踪。

子服务器跟踪请求将以下列形式到达：子服务器跟踪请求将 subreq action 字段设置为 TRACE 常量，将 subreq object 字段设置为子服务器的子服务器代码点来发送状态。跟踪操作使用 parm1 来指示 LONGTRACE 或 SHORTTRACE，使用 parm2 来指示 TRACEON 或 TRACEOFF。

当子系统接收到 parm1 设置为 SHORTTRACE 且 parm2 设置为 TRACEON 的跟踪子服务器数据包时，子系统应该打开子服务器短跟踪。相反，当子系统接收到 parm1 设置为 LONGTRACE 且 parm2 设置为 TRACEON 的跟踪子服务器数据包时，子系统应该打开子服务器长跟踪。当子系统接收到 parm2 设置为 TRACEOFF 的跟踪子服务器数据包时，子系统应该关闭子系统跟踪。

响应刷新请求

支持子系统刷新请求依赖于子系统。选择支持 refresh 命令的子系统程序员应该以下列方式为他们的子系统编写程序，以与 SRC 相互作用：

子系统刷新请求将使得 subreq 结构 action 字段设置为 REFRESH 常量，subreq 结构 object 字段设置为 SUBSYSTEM 常量。刷新子系统操作不使用 parm1 或 parm2。

子系统接收到刷新请求时，子系统应该重新配置其本身。

给 SRC 定义子系统

子系统作为子系统对象被定义到 SRC 对象类。子服务器作为子服务器类型对象被定义在 SRC 配置数据库中。与每种对象类型关联的结构被预先定义在 sys/srcobj.h 文件中。

使用 mkssys 命令或 addssys 子例程创建子系统对象。使用 mkserver 命令创建子服务器类型对象。不需要使用配置命令和子例程指定所有可能的选项和参数。SRC 提供预先设置的缺省值。只必须指定必填的字段和任何希望使用其它值（非缺省值）的字段。请参阅&quot;SRC 对象&quot;的子系统对象类中的&quot;子系统对象描述符和缺省值&quot;表，获取子系统和子服务器缺省值的列表。

通过编写 shell 脚本，可以在命令行添加或修改描述符。也可以使用 C 接口添加或修改它们。命令和子例程可用于配置和修改 SRC 对象。

注意：提供的编程接口选项仅出于方便起见。

请在命令行使用以下命令：

mkssys 向 SRC 配置数据库添加子系统定义。

mkserver 向 SRC 配置数据库添加子服务器定义。

chssys 更改 SRC 配置数据库中的子系统定义。

chserver 更改 SRC 配置数据库中的子服务器定义。

rmssys 从 SRC 配置数据库除去子系统定义。

rmserver 从 SRC 配置数据库除去子服务器定义。

当使用 C 接口时，请使用以下子例程：

addssys 向 SRC 配置数据库添加子系统定义

chssys 更改 SRC 配置数据库中的子系统定义

defssys 使用缺省值初始化新的子系统定义

delssys 从 SRC 配置数据库中删除现有的子系统定义

注意：和 chssys 子例程一起运行的对象代码必须和组系统一起运行。

getssys 从 SRC 配置数据库获取子系统定义

getsubsvr 从 SRC 配置数据库获取子服务器定义

mkssys 和 mkserver 命令内部调用 defssys 子例程以在添加或修改命令行中输入的任何值之前，确定子系统和子服务器的缺省值。

当 SRC 主程序或子系统程序需要检索 SRC 配置文件的数据时，使用 getssys 和 getsubsvr 子例程

其它 SRC 子例程列表

使用以下子例程对使用 SRC 的通信和由 SRC 控制的子系统进行编程：

src_err_msg 返回由 SRC 库例程遇到的 SRC 错误消息文本。

（另见多线程安全版本 src_err_msg_r）

srcsbuf 按可打印格式请求子系统的状态。

另见多线程安全版本 srcsbuf_r）

srcsrqt 发送消息或请求至子系统。

（另见多线程安全版本 srcsrqt_r）

srcstat 请求简短的子系统状态。

另见多线程安全版本 srcstat_r）

srcstathdr 获取 SRC 状态的标题文本。

srcstattxt 获取 SRC 状态码的文本说明。

（另见版本多线程安全版本 srcstattxt_r）

srcstop 请求子系统终止。

srcstrt 请求子系统启动。

CLI

8.softeware installation

http://blog.itpub.net/20444553/viewspace-1009416/

AIX命令集锦八（软件安装命令）

8.1、软件产品的基本概念：lpp(licensed program product 得到许可的软件产品)，它是由一个或多个package(软件包)组成的软件产品的构成：文件集（fileset），软件包（package），得到许可的软件产品（LPP），软件束（bundle）文件集:是AIX中最小的可安装的、能实现特定功能的基本单元，如bos.net.nfs.client软件包 ：是由一组具有共同功能的文件集而组成的一个可单独安装的映像，以BFF(backup file format)格式存在。如bos.net得到许可的软件产品： 由一个或多个软件包构成一个完整的LPP，如bos软件束：是一个软件列表文件，这个列表包含为实现某个特殊用途的文件集、软件包、和得到许可的软件产品，文件名以.bnd结尾软件产品的命名格式：LPP.package.fileset.suffix 其中suffix为后缀软件产品的版本格式：versionnumber.releasenumber.modificationlevel.fixlevelversionnumber 主版本号releasenumber 发布号，即次版本号modificationlevel 修正级别fixlevel 修订级别安装后的软件在AIX中有两种状态：applied(暂时应用状态，即保留旧版本，可以恢复到旧版本)，committed(提交确认状态，即不保留旧版本)一个软件产品的文件集可以划分为3个部分：root,usr,share部分usr部分 包含着软件中可以被其他具有相同硬件体系结构的机器共享的部分，通常保存在/usr目录中root部分 包含着软件中不能被其他机器共享的部分，一般保存在/目录中share部分 包含着软件可以被其中任意一台机器共享的部分，即使它们不拥有相同的硬件体系结构。一般保存在/usr/share目录中。

修订包分类：PTF、APAR、维护包和推荐维护包，其中PTF、APAR是对文件集的修订，维护包和推荐维护包包含着大量的PTF和APAR，主要是对操作系统的修订PTF 是指文件集的可单独安装的更新包（fileset update）,它的作用是增强以前安装的fileset的功能或更正以前fileset的小错误APAR（authorized program analysis report 经授权的软件分析报告） 是针对系统中少见的问题而发布的紧急的软件修订包，对操作系统而言是单一性的错误问题。维护包 （Maintenace package）:对系统的预防性维护由一个维护级别（maintenance level，简写ML）来提供。每次应用一个维护包，就会调整文件集的修正级别modificationlevel，同时将修订级别设置为0,维护包的名称由4个数字组成VRMF,V表示操作系统的主版本，R表示操作系统的次版本，M表示修正级别，F表示修订级别，F一般为0。推荐维护包（recommended maintenance package 简写RML）:指从最新的维护级别之后发布的一组APAR，格式为VRMF-RM

8.2、软件安装命令：installp 是安装和更新软件的命令，该命令的用法在此不详讲smit install 会出现四大功能：install and update software (安装和更新软件)list sofeware and related information (显示软件列表和相关信息)software maintenance and utilities (软件维护和实用工具)network installation management (网络安装管理)我们可以使用smit install_latest命令来进行软件安装，其实它是调用installp命令来执行安装操作的，执行完这条命令后，会出现以下项目：(1)、input device /directory for software  表示要安装的软件所在的目录或驱动器(2)、software to install  该栏的默认值为_all_latest，表示安装所有的软件(3)、preview only? 表示是否对软件进行预安装，即做安装检查，不会执行真正的安装(4)、commit software updates? 表示是否提交新软件（不可恢复）,如果设置为no则是apply新软件，即会保留原来的软件，可以恢复旧软件。(5)、save replaced files 表示是否覆盖旧软件，如果设置为yes就表示保留旧软件，可以用来恢复旧软件(6)、automatically install requisite software ? 表示是否自动安装所必需的软件，即安装的软件所依赖的软件(7)、extend file systems if space needed? 表示文件系统空间不够时，是否自动扩充空间(8)、overwrite same or newer versions? 表示是否覆盖相同版本或较新的版本软件(9)、verify install and check file sizes? 表示是否要求系统对要安装的软件做一些检查(10)、include corresponding language filesets? 表示安装时是否包括相应语言文件集(11)、detailed output? 表示是否需要输出明细的安装信息(12)、process multiple volumes? 是否打开多卷CD的处理，即是否安装文件集存放在多张CD上(13)、accept new license agreements? 表示是否接受软件许可协议，如果选no表示拒绝接受并取消安装(14)、preview new license agreements? 表示是否预览新的许可协议

安装软件束命令：软件束（bundle）：不是真正的文件集，它是一个包含了许多文件集名称的文本文件，系统先查找软件束文件，再从安装介质上查找软件束所包含的文件集，找到后就安装。smit install_bundle

8.3、显示软件列表命令：显示包括两种情况，一种是显示系统中已经安装的软件，一种是显示安装介质中的软件显示在系统中已经安装的文件集和更新文件集：lslpp {-d|-f|-h|-I|-L|-l|-p}[-B|-I][-acJq][-O{[r][s][u]}] [fileset...|ptf_id...|all]lslpp -E[c][fileset...|all]-a 和其他参数结合使用，显示文件集的附加信息。不能和-f使用，和-l显示所有更新包信息，和-h显示所有安装历史-B 允许输入ptd_id，不能与-L结合使用-c 用:号分开输出信息，不能和-La,-J同时使用-d 显示指定软件所要依赖的文件集-E 显示软件许可协议-f 显示文件集中的文件名字，不能跟-a同时使用-h 显示软件安装历史信息，不能和-J同时使用-I 限制输入的软件产品-i 显示软件产品的标识信息-J 输出的信息符合smit所要求的格式，不能和-l，-L同时使用-L 显示文件集的名字、最新版本、状态和描述，将文件集的root,user,share三部分分别显示-O 该参数后跟r,s,u参数，r只显示root部分，s只显示share部分，u只显示user部分，不能和-L同时使用-p 显示被安装文件集所需要的信息-q 输出结果中不显示各列的标题部分-w 显示拥有这个文件的文件集。all 显示所有的文件集参数d,f,h,i,L,l,p,w和E之间是相互排斥的，不能同时使用。lslpp -l 显示中的文件集的状态主要包括：APPLIED  表示暂时应用在系统中APPLYING 正在应用指定的文件集，还没有成功地完成，也不能执行清除操作BROKEN 坏掉的或者被中断安装的软件COMMITTED 确认提交COMMITTING 正在提交指定的文件集，还没有成功地完成，也不能执行清除操作OBSOLETE 陈旧的软件，只把部分文件集移植到新版本REJECTING 正在拒绝（删除）指定的文件集，还没有成功地完成，也不能执行清除操作显示已经安装的软件也可以用smit list_installed_sw显示暂时应用而未确定确认提交的软件的命令smit list_applied_sw,也可用installp -s来显示显示软件安装历史的命令：smit show_history 即显示软件是什么时候安装的，是暂时还是确认提交的，也可以用lslpp -h 文件集名显示安装介质上的软件命令：smit list_media_sw,也可以使用installp -l -d /dev/cd0查找某个文件或命令所对应的文件集的几种方法，前提：系统中必须安装了bos.content_list文件集(1)、通过which_fileset命令，格式为：/usr/sbin/which_fileset [filename/command](2)、lslpp -w [filename/command] 如lslpp -w /usr/bin/ls(3)、lslpp -f [filesetname] 查看文件集包含哪些文件，如lslpp -f bos.acct

8.4、调整软件在系统中的状态命令：软件安装在系统中有两种状态：applied(暂时应用状态)、committed(确认提交状态)，installp也可以调整已经安装软件的状态installp -cgx all 表示提交所有暂时应用的软件，同时删除该软件包以前的版本可以用smit commit来操作拒绝暂时应用的软件命令：smit reject 或installp -rbpX 软件包名 ，如installp -rbpX bos.net从系统中删除软件命令：smit remove 或installp -u 文件集名,如installp -u bos.net.tcp.server

8.5、检查当前系统中软件的维护级别命令：lslpp -l 检查当前系统的维护级别命令：oslevel检查当前系统的RML（推荐维护包）命令：oslevel -r检查某一个APAR是否安装在系统中的命令（首先要知道APAR号，假如是IY32749）：instfix -i -k IY32749instfix 命令能够判断某个修订包是否安装在系统中，该命令的格式为：instfix [-k keyword][-i][-c][-q][-t type][-v][-F][-a]-k keyword 表示指定APAR号或关键字，可以为多个，用空格隔开，并且包含在一对引号中-i 与-k ，-f同时使用,显示指定关键字的软件修订包是否安装，仅仅显示相关信息，不执行安装，如果不加这两个参数，则显示所有知道的软件修订包-c 把由-i显示的结果用:号分开-q 指静止模式-t type 与-i使用时，查找指定类型的修订包，type有f表示修订包，p表示预防性的维护包-v 与-i参数使用显示详细的信息-F 如果在系统中没有安装修订包中的所有文件集，就返回失败-a 显示修订包的症状信息，与-i，-k同时使用显示当前系统中已经安装了哪些预防性的维护包命令：instfix -i -t p查看系统中已经安装了哪些维护包命令：instfix -i |grep AIX显示IY32749修订包是否安装在系统中并显示它的所有文件集的命令：instfix -i -k IY32749 -v显示IY32749修订包是否安装在系统中并显示这个修订包纠正了哪些问题症状命令：instfix -i -k IY32749 -a

下载软件修订包：用fixdist工具下载修订包，下载服务器为：service.software.ibm.com通过安装fixdist工具，然后运行fixdist便可进行下载，前提是必须已经连接到internet上通过ie下载修订包，在此不再叙述安装修订包gzip -d -c 510103.v1.tar.gz |tar -xvf- 从修订包中提取文件集inutoc /usr/sys/inst.images 创建要安装文件集的目录installp -acgXd /usr/sys/inst.images bos.rte.install 更新安装子系统本身smit update_all 把系统中已经安装的所有软件产品升级到最新的版本smit update_by_fix 或smitty instfix 用smit工具安装修订包

8.6、清除一个失败的安装命令：installp -C [-b][-e LogFile]-C  表示清理以前中断的软件安装和不完整的软件安装-b  表示防止系统在需要时执行bosboot命令-e LogFile 打开时间日志，把installp 命令的所有输出记录到指定的日志文件logfile中

8.7、检验软件命令：lppchk 检查lpp的工具，它通过检查文件的大小、校验值和符号连接等内容，与swvpd中的原始数据进行比较，来发现所存在的问题。lppchk -l &amp;apos;X11*&amp;apos; 检查以X11开头的软件产品名中所有的符号链接lppchk -c X11.fnt 检查包含在X11.fnt中的所有文件lppchk -v 如果安装文件集失败，可能会引起该文件集的/,/usr,/usr/share三部分不一致，该命令就是检查一致性问题，如存在则清除该问题。smit check_files 检查并更新文件大小信息smit verify_install 检验软件安装及其必需的部分

AIX日志参考文档

#### Server {#server}

CPU

基于 AMD Opteron 处理器的 IBM 服务器 /Intel ® Xeon® 处理器

IBM System x (x86)

IBM BladeCenter 刀片服务器

IBM Intelligent Cluster

基于 IBM POWER7 处理器技术 ( AIX 、 IBM i 和 Linux 操作系统 )

IBM Power Systems

IBM Power Blade Express 服务器

基于 Z 处理器 :

System z 大型机：一种异构的计算系统，可以托管多种集成在一起的工作负载，每个系统都经过优化，为满足在 IT 基础架构中作为单个实体来管理的个别业务目标。

Power Systems

**Power Systems 硬件** **:**

  ·        

[\\\\\\\\\\\\\\\\l &quot;ps700&quot;](http://www-03.ibm.com/systems/cn/bladecenter/hardware/servers/index.shtml) **刀片服务器**

BladeCenter PS 刀片可交付不断变化的基础结构，帮助快速灵活地交付卓越的业务和 IT 服务 - 均以易于管理的高效方式进行。

[Express](http://www-03.ibm.com/systems/cn/power/hardware/express.shtml)

Power Express 服务器性能卓越，作为用于 UNIX 、 IBM i 和 Linux 工作负载的可靠且安全的分布式服务器、整合服务器或独立服务器。作为带有 4 - 32 个内核的 2U 、 4U 或塔式包装， Power Express 服务器可提供卓越的性能，同时帮助减少基础架构成本和能源成本。

System Z

针对 IBM 大型机的操作系统

z/OS （英文）

z/OS 是基于 64 位 z/Architecture 的健壮的操作系统。它为企业的事务和数据提供最高品质的服务，并将这些品质扩展到使用最新软件技术的新应用程序上。它提供了高度安全、伸缩性强、高性能的平台，在此基础上，您可以构建和部署支持因特网和 Java 的应用程序，从而提供一个综合且多样化的应用程序执行环境。

z/OS.e

z/OS.e 以诱人的价格为 z890 和 z800 提供精心挑选的 z/OS 功能。这是特价产品，衍生自和 z/OS V1R3 相同的代码库，旨在帮助客户开拓快速增长的下一代电子商务领域。

**Linux on System z**

Linux on System z 将 IBM 大型机的优点和 Linux 操作系统的开放标准的灵活性结合起来。Linux 之所以能够在 IT 基础结构简化的工作中扮演主要的角色 － 不仅仅是因为它能够通过使用开放的行业标准帮助简化业务集成，而且还支持更快地部署新的解决方案，并能加快上市时间。

z/VM

a VM hypervisor based on 64-bit z/Architecture, and now with multi-system virtualization and virtual server mobility.

z/VM 提供高度灵活的测试环境和生产环境，帮助企业部署最新的电子商务解决方案。z/VM 构建在坚实的 VM/ESA 基础上，具有广泛的操作系统支持，帮助企业满足不断增长的多系统服务器解决方案需求，支持的操作系统包括 z/OS、OS/390、TPF、z/VSE、CMS、Linux for S/390 或 Linux for System z。

**Z/TPF**

z/Transaction Processing Facility Enterprise Edition (z/TPF) V1.1 (5748-T15) is a high-performance operating system specifically designed to provide high availability for demanding high volume, real-time transaction processing for mission critical e-business applications. z/TPF runs on and exploits IBM&amp;apos;s zSeries servers, an infrastructure offering for transaction processing with high quality of service demands.

多年来，TPF 始终是大多数 IBM 最大客户的&quot;高容量事务处理&quot;（HVTP）平台的首选。这些客户涉及各行业，包括航空、货运、金融、卫生保健和旅游。

z/VSE

z/Virtual Storage Extended (z/VSE)

我们鼓励客户将 VSE 系统升级到最新版本 － z/VSE V3R1。z/VSE 是针对安装了 VSE/ESA 客户的后续产品，被视为未来 VSE 发展的基础。z/VSE 旨在利用所选的 IBM System z 和 IBM TotalStorage 技术，帮助满足 VSE 客户的需求。z/VSE 始终关注互操作性。我们对于 VSE/ESA V2.6 的服务，将于 2006 年 3 月 31 日停止