## services {#services}

#### sysv-rc-conf {#sysv-rc-conf}

SYSV-RC-CONF(8)                                                                                                    SYSV-RC-CONF(8)

NAME

      sysv-rc-conf - Run-level configuration for SysV like init script links( 查看/修改不同运行级别的启动项 )

SYNOPSIS

      sysv-rc-conf [ options ]

      sysv-rc-conf  --list  [ service ]

      sysv-rc-conf [ --level levels ] service &lt;on|off&gt;

#### update-rc.d {#update-rc-d}

UPDATE-RC.D(8)                                                sysv-rc                                               UPDATE-RC.D(8)

NAME

      update-rc.d - install and remove System-V style init script links

SYNOPSIS

      update-rc.d [-n] [-f] name remove

      update-rc.d [-n] name defaults [NN | SS KK]

      update-rc.d [-n] name start|stop NN runlevel [runlevel]...  .  start|stop NN runlevel [runlevel]...  . ...

      update-rc.d [-n] name disable|enable [ S|2|3|4|5 ]

DESCRIPTION

添加启动项，例如mysql

qii@ubuntu:/etc/rc2.d$ sudo update-rc.d mysql defaults

update-rc.d: warning: /etc/init.d/mysql missing LSB information

update-rc.d: see &lt; [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) &gt;

Adding system startup for /etc/init.d/mysql ...

  /etc/rc0.d/K20mysql -&gt; ../init.d/mysql

  /etc/rc1.d/K20mysql -&gt; ../init.d/mysql

  /etc/rc6.d/K20mysql -&gt; ../init.d/mysql

  /etc/rc2.d/S20mysql -&gt; ../init.d/mysql

  /etc/rc3.d/S20mysql -&gt; ../init.d/mysql

  /etc/rc4.d/S20mysql -&gt; ../init.d/mysql

  /etc/rc5.d/S20mysql -&gt; ../init.d/mysql

删除启动项

qii@ubuntu:/etc/rc2.d$ sudo update-rc.d -f mysql remove

Removing any system startup links for /etc/init.d/mysql ...

  /etc/rc0.d/K20mysql

  /etc/rc1.d/K20mysql

  /etc/rc2.d/S20mysql

  /etc/rc3.d/S20mysql

  /etc/rc4.d/S20mysql

  /etc/rc5.d/S20mysql

  /etc/rc6.d/K20mysql

[编辑] rcconf

#### rcconfig {#rcconfig}

RCCONF(8)                                                Debian GNU/Linux                                                RCCONF(8)

NAME

      rcconf - Debian Runlevel configuration tool

SYNOPSIS

      rcconf [options]