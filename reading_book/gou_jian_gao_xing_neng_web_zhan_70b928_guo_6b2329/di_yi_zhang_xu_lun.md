### 第一章 绪论

1.1 等待的真相

当用户输入URL后，等待的时间分为：

a.数据在网络上传输数据的时间；

b.服务器处理请求并生成相应数据的时间；

c.浏览器本地计算和渲染的时间；

1.2瓶颈在那里：

1.3增加贷款

a.设计更加简单的页面，使其包含较少的图片和脚本，但是这可能牺牲了美观和用户交互。

b.将多个图片合并为一个文件，利用CSS背景图片的偏移技术呈现在网页中，避免了图片的下载。

c.合并JavaScript脚本或者CSS样式表。

d.充分利用HTTP中的浏览器端Cache策略，减少重复下载。

1.5加快服务器脚本计算速度

APS.NET/JSP均有内置优化方案，比如解释器对脚本对某个脚本程序第一次解释的时候，将中间代码缓存起来，以供下次直接使用。

PHP使用第三方APC组件

1.6使用动态内容缓存

将动态内容的HTML输出结果缓存起来，在随后的一段时间内当有用户访问时便跳过重复的动态内容计算而直接输出。

1.7使用数据缓存

1.8将动态内容静态化

1.9更换web服务器软件

1.10页面组件分离

1.11合理部署服务器（ISP，CDN）

1.12使用负载均衡

1.13优化数据库

1.14考虑可扩展性

1.15减少视觉等待

不要在用户等待的时候不礼他！