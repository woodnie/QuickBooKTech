## [npm - 设置代理和镜像](https://www.cnblogs.com/wzcblogs/p/6543935.html) 1 {#npm-1}

1.设置http类型的服务器的代理

$ npm config  set  proxy http: //server :port

2.设置https类型的服务器的代理

$ npm config  set  proxy https: //server :port

3.设置npm镜像

$ npm config  set  registry  &quot;http://registry.npmjs.org/&quot;

$ npm config  set  registry  &quot;http://registry.npm.taobao.org/&quot;

4.使用nrm管理npm镜像

安装nrm

$ npm install -g nrm

列出可用镜像

$ nrm ls

使用淘宝镜像

$ nrm use taobao