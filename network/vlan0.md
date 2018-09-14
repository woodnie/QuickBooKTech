## VLAN0 {#vlan0}

vlan0表示**优先级标示帧，**一直记得这个概念，但不能理解

啥是优先级帧？交换机中怎么使用？怎么转发？这几个问题搜索下，发现还是外文网站解释的清晰，特地记录一下。

首先解释为啥要有优先级帧

802.1Q定义了vlan的标准，包括type(16bit)、priority(3bit)、cfi(1bit)、vlan(12bit)

802.1P是802.1Q的子标准，定义了priority的值含义。想象一下，如果我发出一个报文，不知道自己所属的vlan，只想带802.1P优先级信息，应该怎么办？

这时候vlan0就有用武之地了，发出去一个vlan0的tag报文。当交换机收到一个vid为0的报文，就可以认为vlan值无效，不能用于转发，而priority的3bit有效，可以用于优先级映射和调度。

交换机中对vlan的转发处理，各个厂商实现都有差异，一般来说认为是untag，加上端口的pvid后进行转发处理：

CISCO：When these frames are received at the ISP end, the header is stripped off and the frame is processed as per the configuration of the 802.1P priority bits.

一句话，vlan0报文是只带有优先级信息，而无vlan id的报文。