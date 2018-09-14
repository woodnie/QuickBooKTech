#### paloalto {#paloalto}

[http://www.paloaltonetworks.com/](http://www.paloaltonetworks.com/)

Palo Alto Networks&amp;apos; Next-Generation Firewalls

Palo Alto 防火墙不是一台UTM。Gartner称之为&quot;下一代防火墙&quot;。虽然它也像一台单独的IPS、反垃圾邮件、UTL过滤多功能设备一应运转，但是他们有两点主要的不同。

第一，所有这些功能特性可以同时打开而不影响设备的处理性能。它充分利用多线程技术和多核处理器性能同时对穿过防火墙的数据做各种检验处理和过滤操作。而传统的UTM设备先检查URL，再检查AV，，这样依次下去，这样，当各个特性都打开时，传统UTM的性能自然就会大幅下降。

第二点是Palo Alto防火墙与传统防火墙最显著的不同，Palo Alto防火墙首先基于应用签名过滤流量，而不是像传统防火墙那样仅仅基于端口号。也就是说，80端口和http流量不是直接相关的。任意端口上的web 流量，无论它是聊天软件流量、文件传输流量或者bt及语音流量，都可以得到相应检查。端口号码并不是关键。

这是一个巨大的进步，传统防火墙并不能从web流量中区分出Farmville应用的流量(Farmville是一个来自Facebook网站提供的应用，它基于80端口，提供一些股票市场的信息)。而现在，你可以制定策略来允许web流量但是关闭Farmville应用。