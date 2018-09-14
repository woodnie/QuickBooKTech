### Debian/Ubuntu: {#debian-ubuntu}

shadowsocks-libev is available in the official repository for Debian 9(&quot;Stretch&quot;), unstable, Ubuntu 16.10 and later derivatives:

sudo apt update

sudo apt install shadowsocks-libev

For Debian Jessie users, please install it from jessie-backports:

sudo sh -c &#039;printf &quot;deb http://httpredir.debian.org/debian jessie-backports

main&quot; &gt; /etc/apt/sources.list.d/jessie-backports.list&#039;

sudo apt-get update

sudo apt-get -t jessie-backports install shadowsocks-libev