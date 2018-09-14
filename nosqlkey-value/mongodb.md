## MongoDB {#mongodb}

MongoDB 学习笔记(一) MongoDB介绍及安装

[http://www.cnblogs.com/lipan/archive/2011/03/08/1966463.html](http://www.cnblogs.com/lipan/archive/2011/03/08/1966463.html)

1.安装

第一步：下载安装包：官方下载地址←单击此处,如果是win系统，注意是64位还是32位版本的，请选择正确的版本。

第二步：新建目录&quot;MongoDB&quot;，解压下载到的安装包，找到bin目录下面全部.exe文件，拷贝到刚创建的目录下。

第三步：在&quot;MongoDB&quot;目录下新建&quot;data&quot;文件夹，它将会作为数据存放的根文件夹。

2.启动Mongo服务端:

&gt;mongod --dbpath &quot;C:\Program Files\mongodb\data&quot;   # --dbpath指定datafile路径

在浏览器输入： [http://localhost:27017/](http://localhost:27017/)

You are trying to access MongoDB on the native driver port. For http diagnostic access, add 1000 to the port number

3.

&gt;mongo                                    #MongoDB工具

MongoDB shell version: 2.0.2     #MongoDB版本

connecting to: test                    #默认连接MongoDB的test数据库

&gt; help     #键入help可以获取帮助