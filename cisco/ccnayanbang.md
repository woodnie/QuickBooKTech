## CCNA(YanBang) {#ccna-yanbang}

厨房地砖耐脏,耐滑;

厨房一定要插座多(单开带五孔);

#### 第零章 课程引导

router 型号：

800-1800   serise

2600       serise

2800-2900  serise

3900       serise

7900       serise

12000      serise    (国家级骨干网)

switch型号：

2900 serise

3500 serise

3700 serise

4500 serise

6500 serise

7000 serise

案例1.路由器密码破解

1.1 以console方式连接到路由器

1.2 重启路由器

1.3 Ctrl+Break  (TinkPad E40:FN+B＝BREAK键，FN+P=PAUSE键)

1.4进入rommon 1&gt;confreg 0x2142    #

rommon管理：硬件，存储体

路由器启动过程由寄存器（ config-register）的值决定：

0x2102 正常启动（启动OS并加载配置）

0x2142 正常启动（启动OS不加载配置）

1.5进入rommon 2&gt;reset   #重启路由器

1.6

Router#show startup-config #系统保存的配置，既启动后会默认加载的配置

Router#show runing-config  #系统当前运行时配置

Router#copy startup-onfig running-config

Router#conifguer terminal

Router(config)#line console 0

Router(config-line)#no password

Router(config-line)#exit

Router(config)#exit

Router#copy running-config startup-config

Router#conifg-register 0x2102

案例2.OS升级

TFTPserver:192.168.254.254

Router#show version #当前运行的OS版本

Router#show flash    #flash中的OS版本

Router# configure

Router(config)#interface fastEthernet 0/0

Router(config-if)#ip address 192.168.254.1 255.255.255.0

Router(config-if)#exit

Router(config)#exit

Router#copy tftp: flash:

...192.168.254.254

...NEW.bin

...remove all file

Router#copy

Router#reload

案例3.图形化管理

Cisco SDM（Security Device Manager）

Router#configure

Router(config)#username admin privilege 15 password cisco #创建用户admin密码cisco,权限15

Router(config)#ip http authen local        #开启http本地数据库认证

#### 第一章 管理Cisco路由器 {#cisco}

第一节 路由器基本指令