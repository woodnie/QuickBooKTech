## VMware Workstation {#vmware-workstation}

扩展磁盘：

D:\Program Files\VMware\VMware Workstation&gt;vmware-vdiskmanager.exe -x 10GB &quot;I:\My Virtual Machines\Red Hat Enterprise Linux\Red Hat Enterprise Linux 5(A)\Red Hat Enterprise Linux 5.vmdk&quot;

我这里的10G是指增加后的大小，如果小于原始大小就会报错   One of the parameters supplied is invalid .

官方文档： [http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1647](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1647)

vmware-vdiskmanager:

Usage: vmware-vdiskmanager.exe OPTIONS &lt;disk-name&gt; | &lt;mount-point&gt;

Offline disk manipulation utility

 Options:

    -c                   : create disk; need to specify other create options 创建虚拟磁盘,需要与附加选项(-a, -s 和 -t)共同使用

    -d                   : defragment the specified virtual disk 磁盘碎片整理,只能整理可增长的虚拟磁盘,不能整理预分配的虚拟磁盘

    -k                   : shrink the specified virtual disk 压缩指定的虚拟磁盘 只能够收缩可增长磁盘,不能够收缩有虚拟机快照的虚拟磁盘

    -n &lt;source-disk&gt;     : rename the specified virtual disk; need to（重命名指定磁盘，需要标明改变后的磁盘名称）specify destination disk-name

    -p                   : prepare the mounted virtual disk specified by

                           the drive-letter for shrinking

                           为收缩磁盘做准备处理。如果虚拟磁盘被分成多个分区，每个分区必须被单独准备。分区（比如C：或D：）

                           必须用VMware DiskMount工具映射。在你对分区准备处理后，解除对此分区的映射。继续映射虚拟磁盘的其他

                            每个分区，为收缩磁盘作准备处理直到完成虚拟磁盘上的所有分区的准备工作。在同一时刻只能用

                            VMware DiskMount映射虚拟磁盘的一个分区。你仅仅能在Windows宿主机上进行虚拟磁盘的收缩分区准备工作。

    -q                   : do not log messages  禁止虚拟磁盘管理程序写日志，如果你允许记录日志，日志将会被虚拟磁盘管理程序产生

                            并储存。在虚拟磁盘管理程序运行后，日志的名字和存放位置将会出现在命令行或终端中。

    -r &lt;source-disk&gt;     : convert the specified disk; need to specify 转换指定磁盘，需要标明转换后磁盘的类型

                           destination disk-type

                           例如： vmware-vdiskmanager -r sourceDisk.vmdk -t 0 targetDisk.vmdk

                           这个命令将转换磁盘从它的原始的预分配模式转变为包含在单一文件中的可增长虚拟磁盘。这个虚拟磁盘空间将不会

                           被预先分配，虚拟磁盘工具将收回虚拟磁盘中的一些磁盘空间，而仅仅让里面的数据占用虚拟磁盘空间。

    -x &lt;new-capacity&gt;    : expand the disk to the specified capacity 将磁盘扩展到指定大小

创建及转换磁盘的附加选项：Additional options for create and convert

       -a &lt;adapter&gt;      : (for use with -c only) adapter type (ide, buslogic or lsilogic) 指定磁盘适配器

       -s &lt;size&gt;         : capacity of the virtual disk 指定磁盘大小

       -t &lt;disk-type&gt;    : disk type id 指定磁盘类型，与磁盘适配器搭配使用

                    Disk types:

                               0  : single growable virtual disk 创建一个包含在单一虚拟文件中的可增长虚拟磁盘

                               1  : growable virtual disk split in 2Gb files 创建一个被分割为每个文件2GB大小的可增长虚拟磁盘

                               2  : preallocated virtual disk 创建一个包含在单一虚拟文件中的预分配虚拟磁盘

                               3 : preallocated virtual disk split in 2Gb files 创建一个被分割为每个文件2GB大小的预分配虚拟磁盘

    The capacity can be specified in sectors, Kb, Mb or Gb. 容量单位

    The acceptable ranges:

                          ide adapter : [100.0Mb, 950.0Gb] 磁盘容量大小限制，跟适配器类型相关,IDE和SCSI适配器都为最小100MB，最大950GB。

                          scsi adapter: [100.0Mb, 950.0Gb]

举例来说明它的用法：

       ex 1: vmware-vdiskmanager.exe -c -s 850Mb -a ide -t 0 myIdeDisk.vmdk               #创建一个命名为myIdeDisk,大小为850M，适配器类型为ide的单增长磁盘

       ex 2: vmware-vdiskmanager.exe -d myDisk.vmdk                                                       #整理myDisk的磁盘碎片

       ex 3: vmware-vdiskmanager.exe -r sourceDisk.vmdk -t 0 destinationDisk.vmdk

       ex 4: vmware-vdiskmanager.exe -x 36Gb myDisk.vmdk                                             #把myDisk的大小扩展至36GB

       ex 5: vmware-vdiskmanager.exe -n sourceName.vmdk destinationName.vmdk      #重新命名

       ex 6: vmware-vdiskmanager.exe -k myDisk.vmdk   #压缩磁盘,收缩磁盘时会产生一个临时文件,其实它就是收缩后的虚拟磁盘文件,会代替原来的那个虚拟磁盘文件

       ex 7: vmware-vdiskmanager.exe -p &lt;mount-point&gt; 为收缩虚拟磁盘做准备

                (A virtual disk first needs to be mounted at &lt;mount-point&gt;)