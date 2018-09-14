#### robots.txt {#robots-txt}

例子

让所有机器人访问所有文件，因为通配符&quot;*&quot;代表所有机器人：

User-agent: *

Disallow:

拦截所有的机器人：

User-agent: *

Disallow: /

禁止所有机器人访问特定目录：

User-agent: *

Disallow: /cgi-bin/

Disallow: /images/

Disallow: /tmp/

Disallow: /private/

仅禁止坏爬虫访问特定目录（BadBot用真实的名字代替）：

User-agent: BadBot

Disallow: /private/