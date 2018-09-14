## /etc/security/access.conf {#etc-security-access-conf}

有几种技术可以用来限制普通用户切换到超级用户身份的途径。举例来说，

PAM（参见1.9节）控制着登录用户、登录时间和登录方式。

通过/etc/securetty文件可以控制用户从哪些终端（tty）登录才能具有root身份。

/etc/security/access.conf文件为登录控制添加了另一种控制尺度