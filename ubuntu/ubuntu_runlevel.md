## ubuntu runlevel {#ubuntu-runlevel}

1\. 在debian和ubuntu中，并没有存在/etc/inittab文件。系统的默认运行级别是通过/etc/event.d/rc-default文件来设置的。不过为了兼容，如果用户自行建立/etc/inittab文件，那么/etc/event.d/rc-default脚本会进行检测并且按照inittab文件中的设置来设置系统运行级别。

/etc/inittab 文件中设置的，具体的设置如下：

id:N:initdefault：

Ubuntu 的系统运行级别：

0        系统停机状态

1        单用户或系统维护状态

2~5      多用户状态

6        重新启动

S