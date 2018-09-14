## EMC 统一存储VNX架构简介   {#emc-vnx}

EMC于近日推出了[VNX](http://www.storageonline.com.cn/tag/vnx/)产品线，正式与NetApp的FAS产品线竞争。其中[VNX](http://www.storageonline.com.cn/tag/vnx/)5100只提供块访问，[VNX](http://www.storageonline.com.cn/tag/vnx/)7500为高端产品。

**说实在的，架构没啥大变化，还是2个SP来处理块访问，多个Data Mover来处理文件访问。**

支持的文件访问协议有NFS、CIFS、MPFS和pNFS。程序块访问协议有光纤通道、FCoE和iSCSI。

在文件访问形式中，从5100到7500各款产品的X刀片机控制器的数量依次为0，1到2（外加每个刀片机6GB的系统内存），1到3（外加每个刀 片机12GB的系统内存），2到4（外加每个刀片机12GB的系统内存）和2到8（外加每个刀片机24GB的系统内存）。在程序块访问形式中，存储处理器 的数量并不随产品等级的提高而增加，但是每个存储处理器的内存将从4GB逐渐上升到8GB、12GB、18GB和24GB。

最大的变化是后端从FC-AL变成了SAS，还有了25块盘的DAE。 所有的硬盘都配备了SAS接口，支持企业SAS、近线SAS和固态硬盘。

OS: VNX operating enviroment for file (Clariion FLARE)

OS: VNX operatiing enviroment for block (Cellerra DART)