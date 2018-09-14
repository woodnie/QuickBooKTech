## Garbage characters(zh) {#garbage-characters-zh}

字符界面乱码：字符界面默认不显示中文，全是菱形符号，这样大大限制了中文用户的使用。解决办法如下：

首先安装zhcon：

$sudo apt-get install zhcon

这样我们可以通过启动zhcon来显示中文，但是此时不能直接输入zhcon，否则会黑屏，正确的做法是：

$zhcon -utf8 -drv=vga