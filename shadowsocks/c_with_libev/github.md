### GitHub {#github}

Build and install the project from source codes.

$ sudo apt-get install --no-install-recommends build-essential autoconf libtool \

libssl-dev gawk debhelper dh-systemd init-system-helpers pkg-config asciidoc \

xmlto apg libpcre3-dev zlib1g-dev libev-dev libudns-dev libsodium-dev libmbedtls-dev libc-ares-dev automake

$ git clone https://github.com/shadowsocks/shadowsocks-libev.git

$ cd shadowsocks-libev

$ git submodule update --init

$ ./autogen.sh &amp;&amp; ./configure &amp;&amp; make

$ sudo make install

shadowsocks-libev is licensed under the [GNU General Public License v3.0](https://www.gnu.org/copyleft/gpl.html).