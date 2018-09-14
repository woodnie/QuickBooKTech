## telnet {#telnet}

本地启动一个 Tomcat 做为测试 然后命令行下输入： telnet localhost 80 然后 ctrl+] ，接下来什么也不要输入直接回车，然后再输入命令就可以看到回显了

##########

1 、打开 &quot; 运行 &quot;-&gt;cmd 进入命令环境； ~~~~~2 、输入 &quot;telnet www.baidu.com 80&quot; ，回车后 , 屏幕为全黑，此时我们利用快捷键 &quot;Ctrl+]( 右中括号 )&quot; 来打开本地回显功能，这样我们就可以看见我们所打的东西了，如图：（注本阶段执行过程和以下的过程均要求操作时间尽可能短，因为时间一长，便会被认为断开连接。）

~~~~~3 、单击回车，进行编辑状态。 ~~~~~4 、输入： &quot; GET / HTTP/1.1&quot; 后回车 , 在第二段接着输入： &quot;HOST:&quot; 然后按回车，这样一个简单的 HTTP 请求就完成了，接着我人只要再按下回车，便向服务器递交这个请求了。如图：（我们来看一下这个是什么意思： GET 表示请求方式， / 表示请求的根目录下的文件， HTTP/1.1 表示 HTTP 协议版本， HOST 就是一个消息头，据某些朋友说 1.1 的版本一定要加一个 &quot;HOST:&quot; 可是我实验后发现 &quot;HOST 不加仍旧可以正常发送请求，但是 GET HTTP 这个必须大写，否则就该请求无法发送）

~~~~~5 、接收服务器返回，这步其实不需要我们来做，因为当我们发送请求后，只需几秒钟，我们便会收到来自服务器反应 .

~

~~~~~6 、这样 , 请求就算完成了。下面我们在百度中搜一下 &quot;1&quot;, 浏览器中的地址应该是 : [http://www.baidu.com/s?wd=1](http://www.baidu.com/s?wd=1) . 看看请求是怎么样的

~~~~~ 怎么样，大家会了吗？以上只是用 GET 方式进行请求，当然还可以用 POST 方式进行请求，只是 POST 我这不方便做实验，所以就不写了。大概的格式给大家参考下： ~~~~~POST /localhost/login.aspx HTTP/1.1~~~~~HOST:~~~~~Content-Type:application/x-www-form-urlencoded~~~~~Content-Length:10~~~~~~~~~~~uid=xxxxxx