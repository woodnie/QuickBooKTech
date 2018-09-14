### http request method {#http-request-method}

GET 和POST的本质区别是什么？

      使用GET，form中的数据将编码到url中，而使用POST的form中的数据则在http协议的header中传输。在使用上，当且仅当请求幂等（字面意思是请求任意次返回同样的结果，本质是请求本身不会改变服务器数据和状态）时使用GET，当请求会改变服务器数据或状态时（更新数据，上传文件），应该使用POST。

区别使用GET，POST意义何在？

     重复访问使用GET方法请求的页面，浏览器会使用缓存处理后续请求。使用POST方法的form提交时，浏览器机遇POST将产生永久改变的假设，将让用户进行提交确认。当编成人员正确的使用GET，POST后，浏览器会给出很好的缓存配合，时响应速度更快。

在form提交阶段的差别

       form提交的第一步是创建数据集，并根据ENCTYPE对数据集进行编码。ENCTYPE有两个值：multipart/form- data，application/x-www-form-urlencoded（默认值），前者可同时用于GET，POST，后者只用于POST。然后进行数据传输--对于GET方法，数据集使用content type application/x-www-form-urlencoded编码并附在url后面，在这种模式下，数据严格限制为ASCII码；对于POST，使用content type编码字符集并将其构造成消息发送。

在服务器处理部分的差别

      原则上，除理GET和POST请求是没有分别的。但由于数据通过不同的方法编码，需要有不同的解码机制。所以，方法变化将导致处理请求的代码变化。比如对于cgi，处理GET时通过环境变量获得参数，处理POST请求时则通过标准输入(stdin) 获得数据。

从使用经验，我们有如下总结：

1、 get是把参数数据队列加到提交表单的ACTION属性所指的URL中，值和表单内各个字段一一对应，在URL中可以看到。post是通过HTTP post机制，将表单内各个字段与其内容放置在HTML HEADER内一起传送到ACTION属性所指的URL地址。用户看不到这个过程。

2、对于get方式，服务器端用Request.QueryString获取变量的值，对于post方式，服务器端用Request.Form获取提交的数据。两种方式的参数都可以用Request来获得。

3、get传送的数据量较小，不能大于2KB。post传送的数据量较大，一般被默认为不受限制。但理论上，IIS4中最大量为80KB，IIS5中为100KB。

4、get安全性非常低，post安全性较高。

5、&lt;form method= &quot;get&quot;action=&quot;a.asp?b=b&quot;&gt;跟&lt;form method=&quot;get&quot; action=&quot;a.asp&quot;&gt;是一样的，也就是说，action页面后边带的参数列表会被忽视；而&lt;form method= &quot;post&quot;action=&quot;a.asp?b=b&quot;&gt;跟&lt;form method=&quot;post&quot; action=&quot;a.asp&quot;&gt;是不一样的。

++++++++++

因为HTTP/1.1是Internet现行的标准协议，这里详细介绍其相关语法。 首先，HTTP/1.1格式可写为： 其中请求方法是请求一定的Web页面的程序或用于特定的URL。可选用下列几种： GET： 请求指定的页面信息，并返回实体主体。 HEAD： 只请求页面的首部。 POST： 请求服务器接受所指定的文档作为对所标识的URI的新的从属实体。 PUT： 从客户端向服务器传送的数据取代指定的文档的内容。 DELETE： 请求服务器删除指定的页面。 OPTIONS： 允许客户端查看服务器的性能。 TRACE： 请求服务器在响应中的实体主体部分返回所得到的内容。 PATCH： 实体中包含一个表，表中说明与该URI所表示的原内容的区别。 MOVE： 请求服务器将指定的页面移至另一个网络地址。 COPY： 请求服务器将指定的页面拷贝至另一个网络地址。 LINK： 请求服务器建立链接关系。 UNLINK： 断开链接关系。 WRAPPED： 允许客户端发送经过封装的请求。 Extension-mothed：在不改动协议的前提下，可增加另外的方法。比如： GET /index.html HTTP/1.1 Accept: text/plain /*纯ASCII码文本文件*/ Accept: text/html /*HTML文本文件*/ User-Agent:Mozilla/4.5(WinNT) 说明浏览器使用Get方法请求文档/index.html。浏览器则只允许接收纯ASCII码文本文件和HTML文本文件，其使用的引擎是Mozilla/4.5（Netscape）。 当服务器响应时，其状态行的信息为HTTP的版本号，状态码，及解释状态码的简单说明。现将5类状态码详细列出： ① 客户方错误 100　 继续 101　 交换协议 ② 成功 200 　OK 201 　已创建 202　 接收 203　 非认证信息 204　 无内容 205 　重置内容 206　 部分内容 ③ 重定向 300 　多路选择 301　 永久转移 302　 暂时转移 303　 参见其它 304 　未修改（Not Modified） 305　 使用代理 ④ 客户方错误 400　 错误请求（Bad Request） 401 　未认证 402 　需要付费 403　 禁止（Forbidden） 404　 未找到（Not Found） 405　 方法不允许 406　 不接受 407　 需要代理认证 408　 请求超时 409　 冲突 410 　失败 411 　需要长度 412　 条件失败 413 　请求实体太大 414 　请求URI太长 415 　不支持媒体类型 ⑤ 服务器错误 500　 服务器内部错误 501　 未实现（Not Implemented） 502　 网关失败 504 　网关超时 505 HTTP版本不支持比如：（在《TELNET……》一文中用telnet登陆80端口,相同的方法用在HTTP/1.1中,会发现没有显示，下面补充说明之） telnet www.fudan.edu.cn 80 HEAD / HTTP/1.1 host:www.fudan.edu.cn /*本行为输入内容*/ HTTP/1.1 501 Method Not Implemented Date: Web, 01 Nov 2000 07:12:29 GMT /*当前的日期/时间*/ Server: Apache/1.3.12 (Unix) /*Web服务器信息*/ Allow: GET, HEAD, OPTION, TRACE /*支持的方法类型*/ Connection: close Connect-Type: Text/html; charset=iso-8859-1/*连接的媒体类型*/ &lt; /FONT&gt;

Method Not Implemented

head to /inde x.html not supported.

Invalid method in request head / htp/1.1