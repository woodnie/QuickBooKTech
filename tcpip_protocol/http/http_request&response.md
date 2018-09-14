### http request&amp;response {#http-request-response}

HTTP 请求和响应格式

HTTP请求格式:

&lt;request-line&gt;

&lt;headers&gt;

&lt;blank line&gt;

[&lt;request-body&gt;]

说明:第一行必须是一个请求行(request-line),用来说明请求类型,要访问的资源以及所使用的HTTP版本.

     紧接着是一个首部(header)小节,用来说明服务器要使用的附加信息.

     之后是一个空行.

     再后面可以添加任意的其他数据[称之为主体(body)].

例1 GET请求:

GET / HTTP/1.1

Accept: */*

Accept-Language: zh-cn

Accept-Encoding: gzip, deflate

User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022)

Host: www.google.cn

Connection: Keep-Alive

说明:请求的第一部分说明了该请求是一个GET请求.该行的第二部分是一个斜杠(/),用来说明请求的是该域名的根目录.该行的最后一部分说明使用的是HTTP1.1版本(另一个可选荐是1.0).

     第2行是请求的第一个首部,HOST将指出请求的目的地.User-Agent,服务器端和客户端脚本都能访问它,它是浏览器类型检测逻辑的重要基础.该信息由你的浏览器来定义,并且在每个请求中自动发送.Connection,通常将浏览器操作设置为Keep-Alive

     第三部分,空行,即使不存在请求主体,这个空行也是必需的.

例2 POST请求:

POST / HTTP1.1

Host:www.wrox.com

User-Agent:Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022)

Content-Type:application/x-www-form-urlencoded

Content-Length:40

Connection: Keep-Alive

name=Professional%20Ajax&amp;publisher=Wiley

说明:请求行开始处的GET改为POST,以表示不同的请求类型.

     Content-Type说明了请求主体的内容是如何编码的.浏览器始终以application/x-www-form- urlencoded的格式编码来传送数据,这是针对简单URL编码的MIME类型.Content-Length说明了请求主体的字节数.

     最后请求主体.名称-值对的形式.

HTTP响应格式:

&lt;status-line&gt;

&lt;headers&gt;

&lt;blank line&gt;

[&lt;response-body&gt;]

例:

HTTP/1.1 200 OK

Date: Fri, 22 May 2009 06:07:21 GMT

Content-Type: text/html; charset=UTF-8

&lt;html&gt;

     &lt;head&gt;&lt;/head&gt;

     &lt;body&gt;

           &lt;!--body goes here--&gt;

     &lt;/body&gt;

&lt;/html&gt;

说明:HTTP状态码200,找到资源,并且一切正常.

     Date:生成响应的日期和时间.

     Content-Type:指定了MIME类型的HTML(text/html),编码类型是UTF-8

     HTML源文体.