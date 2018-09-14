## [npm - 设置代理和镜像](https://www.cnblogs.com/wzcblogs/p/6543935.html) 2 {#npm-2}

内网使用npm很头痛的一个问题就是代理，假设我们的代理是 [http://proxy.example.com:8080，那么命令如下：](http://proxy.example.com:8080%EF%BC%8C%E9%82%A3%E4%B9%88%E5%91%BD%E4%BB%A4%E5%A6%82%E4%B8%8B%EF%BC%9A)

npm config set proxy [http://proxy.example.com:8080](http://proxy.example.com:8080)

由于 npm config set命令比较常用，于是可以如下简写

npm set proxy [http://proxy.example.com:8080](http://proxy.example.com:8080)