## URI and QR code {#uri-and-qr-code}

Shadowsocks for Android / iOS also accepts BASE64 encoded URI format configs:

ss://BASE64-ENCODED-STRING-WITHOUT-PADDING#TAG

Where the plain URI should be:

ss://method:password@hostname:port

Note that the above URI doesn&amp;apos;t follow RFC3986\. It means the password here should be plain text, not percent-encoded.

For example, we have a server at 192.168.100.1:8888 using bf-cfb encryption method and password test/!@#:. Then, with the plain URI ss://bf-cfb:test/!@#:@192.168.100.1:8888, we can generate the BASE64 encoded URI:

ss://YmYtY2ZiOnRlc3RAMTkyLjE2OC4xMDAuMTo4ODg4Cg

To help organize and identify these URIs, you can append a tag after the BASE64 encoded string:

ss://YmYtY2ZiOnRlc3RAMTkyLjE2OC4xMDAuMTo4ODg4Cg#example-server

This URI can also be encoded to QR code. Then, just scan it with your Android / iOS devices: