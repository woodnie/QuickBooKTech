## interface {#interface}

Ubuntu 命令行下的网络配置

编辑 /etc/network/interface文件如下

先添加

auto lo

iface lo inet loopback

auto eth0

如果是自动获取ip，添加

iface eth0 inet dhcp

如果是手动配置ip，添加

iface eth0 inet static

       address xxx.xxx.xxx.xxx

       netmask xxx.xxx.xxx.xxx

       network xxx.xxx.xxx.xxx

       boardcast xxx.xxx.xxx.xxx

       gateway xxx.xxx.xxx.xxx

dns-nameservers 75.75.75.75 75.75.76.76

dns-search local

dns-domain local.domain