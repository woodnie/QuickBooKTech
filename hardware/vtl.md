## VTL {#vtl}

VTL(<sup>[1]</sup> Virtual Tape Library，[虚拟磁带库](http://baike.baidu.com/view/3704654.htm))通常为一种专用的计算工具(Appliance)，它可以仿真物理[磁带库](http://baike.baidu.com/subview/253185/253185.htm)的[驱动器](http://baike.baidu.com/view/15529.htm)和(并且)在磁盘上存储备份映像。VTL允许使用现有的磁带备份软件，管理人员之所以对这些工具感兴趣是因为用于备份管理的范例(paradigm)与使用磁带时的范例相同。

VTL由三部分组件构成： 计算机硬件，通常为[Intel处理器](http://baike.baidu.com/subview/3636620/3636620.htm)(基于Linux操作系统且由该系统供电)，或者相近的变体; 应用软件(用于仿真磁带库和[磁带驱动器](http://baike.baidu.com/subview/3300771/3300771.htm)); 和一组基于RAID技术的[磁盘驱动器](http://baike.baidu.com/view/325542.htm)(在硬盘失效时它们可避免丢失任何数据)。 个别产商常常把这些组件捆绑成一个工具。 然而，也有可能从一家厂商购买计算机硬件和软件，再到另外一家不同的厂商那里购买[磁盘阵列](http://baike.baidu.com/view/63423.htm)。

VTL允许客户配置虚拟磁带驱动器、虚拟磁带盒和指定磁带盒容量。 厂商不同，支持虚拟磁带驱动器的最大数目也不同，变化范围从个位数到无穷。 与物理[磁带库](http://baike.baidu.com/view/253185.htm)不同，物理磁带库需要购买并安装额外的[磁带驱动器](http://baike.baidu.com/subview/3300771/3300771.htm)，但对VTL来说通过改变[软件结构](http://baike.baidu.com/view/600142.htm)(configuration)即可增加虚拟磁带驱动器，而这不需要花费任何额外的硬件成本。

大概可以分为三种类型:磁盘阵列型(Disk Array Based)、应用服务器型(VTL Appliance)、备份软件型(Backup Software)。<sup>[1]</sup>