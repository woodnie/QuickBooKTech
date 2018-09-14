## resolve {#resolve}

原来只需要往resolvconf这个程序的目录里写入一个新配置文件就可以解决。让我们一起看看怎么样在Ubuntu 12.04 LTS Server版中配置自己的DNS服务器吧！

   #vim /etc/resolvconf/resolv.conf.d/base

然后我们在这个文件里写入自己要添加的DNS服务器，格式与以前的/etc/resolv.conf文件一致：

   nameserver 8.8.8.8

   nameserver 8.8.4.4

然后输入wq保存退出。接下来我们重启下resolvconf程序，让配置生效：

   #/etc/init.d/resolvconf restart

再去看看/etc/resolv.conf文件，自己添加的DNS服务器果然乖乖的写进去了！至此问题完美解决！

资料参考： [http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf-ubuntu-12-04](http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf-ubuntu-12-04)