### Docker {#docker}

shadowsocks-libev is shipped also in containers, which makes it a great choice if your cloud provider is Docker-ready or if you aim to build a scalable solution.

docker pull shadowsocks/shadowsocks-libev

docker run -e PASSWORD=&lt;password&gt; -p&lt;server-port&gt;:8388 -p&lt;server-port&gt;:8388/udp -d shadowsocks/shadowsocks-libev

More information about the image can be found [here](https://github.com/shadowsocks/shadowsocks-libev/blob/master/docker/alpine/README.md).