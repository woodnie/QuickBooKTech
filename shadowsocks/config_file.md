## Config File {#config-file}

Shadowsocks accepts [JSON](http://www.json.org/) format configs like this:

{

&quot;server&quot;:&quot;my_server_ip&quot;,

&quot;server_port&quot;:8388,

&quot;local_port&quot;:1080,

&quot;password&quot;:&quot;barfoo!&quot;,

&quot;timeout&quot;:600,

&quot;method&quot;:&quot;chacha20-ietf-poly1305&quot;

}

Explanation of each field:

*   server: your hostname or server IP (IPv4/IPv6).
*   server_port: server port number.
*   local_port: local port number.
*   password: a password used to encrypt transfer.
*   timeout: connections timeout in seconds.
*   method: encryption method.