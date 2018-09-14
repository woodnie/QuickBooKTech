## busybox {#busybox}

busybox ifconfig 192.168.176.222 netmask 25.255.255.0

busybox route add default gw 192.168.176.2

++++++++++++

利用busybox制作一个小巧的linux系统(仅两个文件)

1\. 下载busybox和linux kernel的源码.

busybox的源码地址: [http://www.busybox.net/](http://www.busybox.net/)

linux kernel的源码地址: [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

我选择的busybox版本是: busybox-1.16.0.tar.bz2

linux kernel的版本是: linux-2.6.28.tar.bz2

2\. 接下来我们先编译linux内核

我将下载下来的内核源代码压缩包拷贝到/usr/src目录下，然后进入到这个目录将其解压,命令如下:

# tar xjf linux-2.6.28.tar.bz2

然后创建一个目录，用来保存编译内核产生的目标文件

# pwd

/usr/src

# mkdir linux-2.6.28-obj

执行完上述命令/usr/src目录会有如下图所示:

linux-2.6.28-obj现在是一个空目录，编译内核时会将目标文件输出保存到这个目录下。

linux-2.6.28 是刚才linux-2.6.28.tar.bz2文件解压出来的目录。

然后我们开始编译linux内核,输入如下所示的命令:

# cd /usr/src/linux-2.6.28  (进入到内核源码树目录)

# make O=/usr/src/linux-2.6.28-obj menuconfig (配置内核)

配置内核时，里面的选项有很多,如果不确定的话就将所有选项都编译进内核，当然最好能针对性的配置内核，这样产生出的内核镜像不至于太大。还有一点就是配置时一定要将选定的选项编译进内核，而不要编译成模块。同时，为了支持initrd内存盘文件系统，有两个选项是必须的。

一个是General Setup -&gt; Initial RAM filesystem and RAM disk support

另一个是 Device Drivers -&gt; Block Devices -&gt; RAM block device support

这个选项的子选项保持默认就可以了，如下图所示:

然后退出配置界面，在退出时会提示你是否保存刚才的配置，选择yes就可以了(因为我们在配置时指明了O=/usr/src/linux-2.6.28-obj 目录，所以配置文件会保存到这个目录下，文件名为.config)

接下来我们开始编译内核:

# make O=/usr/src/linux-2.6.28-obj  (生成内核镜像和模块)

通常，我们编译内核是为了更新内核，但这里我们只是为了编译出一个内核镜像，所以就不调用make install命令来安装内核了。

好！内核编译完成，我们将编译好的内核镜像拷贝到主目录下，以供后面使用。

# cp /usr/src/linux-2.6.28-obj/arch/x86/boot/bzImage ~ (拷贝内核镜像到root用户的主目录下)

3.编译busybox

接下来我们开始编译busybox。（我的busybox-1.16.0.tar.bz2存放到了/root目录下）

# tar xf busybox-1.16.0.tar.bz2 (解压busybox压缩包)

# cd busybox-1.16.0 (进入到解压后的busybox源码目录)

# make menuconfig (配置busybox)

注意配置时，一定要选择静态链接选项，该选项位于:

Busybox Settings -&gt; Build Options -&gt; Build Busybox as a static binary

接下来，我们安装busybox

# make install (busybox默认安装到了其源码树目录的名字为_install的目录中)

# cd _install (进入安装了busybox的目录)

当我们进入了busybox后发现了熟悉的linux目录结构，但只有这些是不够的还需要手工添加一些基本的配置文件。

4\. 在busybox中添加配置文件并生成initrd镜像

这时，我们处在/root/busybox-1.16.0/_install 目录下。

好了，开始我们的配置~

# mkdir proc sys etc dev (创建四个空目录，linux内核需要)

# cd dev

# mknod console c 5 1 (创建一个控制台字符设备文件)

# mknod null c 1 3 (创建一个0设备文件)

# cd ..

# cd etc

# vim fstab (输入如下图内容)

# mkdir init.d

# vim init.d/rcS (输入如下内容)

# chmod +x init.d/rcS (给rcS文件加上可执行权限)

# vim inittab (输入如下内容)

# cd ..

# pwd (打印当前目录)

/root/busybox-1.16.0/_install

此时表明我们处在busybox安装文件的根目录下

# rm linuxrc (删除linuxrc链接文件)

然后新创建一个指向busybox文件的链接文件，如下图所示：

我们输入如下图所示命令来创建initrd镜像.

# cd ..

# cp initrd.gz ~ (将其拷贝到主目录)

至此我们就得到了两个镜像文件：

bzImage : linux内核镜像文件

initrd.gz : 内存盘根文件系统镜像文件

好！接下来我们在一个grub引导器下，来引导这个系统：

嗯。为了方便起见，我将生成的这两个文件拷贝到了/boot下

只要在grub提示符下输入如下图所示的三个命令，你的mini linux就能引导开了~~

启动后如下图所示：

参考资料：

1\.   [http://www.ibm.com/developerworks/cn/linux/l-k26initrd/](http://www.ibm.com/developerworks/cn/linux/l-k26initrd/)

2\. 内核源码树里的Documentation/initrd.txt文件

3\. man inittab  

4\. 内核源码树里的README文件

---------------THE END------------