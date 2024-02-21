## Objetivo 

La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30001 en localhost mediante cifrado SSL.

Nota útil: ¿Obtienes “HEARTBEATING” y “Read R BLOCK”? Utilice -ign_eof y lea la sección "COMANDOS CONECTADOS" en la página de manual. Junto a 'R' y 'Q', el comando 'B' también funciona en esta versión de ese comando...

## Datos de acceso al nivel

user bandit15
password - jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
## Solucion

```


bandit15@bandit:~$ nc localhost 30001
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
bandit15@bandit:~$ 



bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Feb 18 10:54:16 2024 GMT
verify return:1
depth=0 CN = localhost
notAfter=Feb 18 10:54:16 2024 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Feb 18 10:53:16 2024 GMT; NotAfter: Feb 18 10:54:16 2024 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEcjY6OTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjQwMjE4MTA1MzE2WhcNMjQwMjE4MTA1NDE2WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCz
TX1NLedZhpQfXiWbWWD2BlNYjANpj+TnzUOI9ZbKJnOQJAbFfWZLA6No7XOStgje
+RPIoAHrX42G95VDfWtRms+qCsCTlUaS9291dZJQ3iOjBIE+PvmRcGdUlFJXDYa6
E61L2DKLbb8YSAnSuUPG3K7CtdxJpA5DpCBCmHEA9t5gZ5HGo9Gt9Kay9lhApX78
ocytwwHG15LplXI6LQB3ykhyCAcfljR3azd90T83dz7kLyM7yIMt60k1kemuX6RW
qSvkCvxmckRFoQPjwKZUopGLlhcC58Kb2xlwEGK+9j/ibBRkmEdBkOOeb5pJol7K
Wkd9LdG0nTWrggni7EKbAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQCA
j53OECoyjZMkHINZj35xk2kKQc9Jj9XjoCE0HlooUWd1ETik/2TkIbdWenozDrgH
10Jqmu/zAEhQkfFALBXCR7Vo0319yvR3rlnC2TdzMeBeUQ/n6ivPsCCL6SF8UTWT
XZJoTEfmp+Ma4zup/mEs23uO/FQ0J3LmSgICtXzPCA09M/ffj2UgTENdTHDltQxl
nQpzF+U40+bg/2PQ83XOTQJbZVbU2FnP/MitSYycxemLJXzbdsIxQhQy0VmTY73E
ZFemHVTbzEzcsCJRak4AyPZ9Zpi2uozHA8r1PqtnDzsN5FBFwuJxCuc+F8QeHh9e
QoyfsotkA6BO0LBqWNvE
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 23FE309B242AB6C447E46B73A3FFBD47D94FF681E6C1EC208189F7CA0D148311
    Session-ID-ctx: 
    Resumption PSK: 8EF1E21D145E641398FB20A61B489F2E0757CB0820371727756B47AD2EBD400E1B2B591826A7793B4DE2E95247B094DD
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - dc 1b 67 7e 6b 49 ec f9-e1 0a 8a 6e cb ac b4 e6   ..g~kI.....n....
    0010 - 2a 11 f4 9a ed fd c5 e1-c6 78 77 93 cc 08 93 e4   *........xw.....
    0020 - 2b 9d fc 28 8c 97 dc 20-c5 1e 8b 60 f9 83 b7 48   +..(... ...`...H
    0030 - 8c 31 e6 85 0c f6 de 98-1f 47 53 b9 be b9 29 21   .1.......GS...)!
    0040 - 47 a6 ec 0a b2 51 37 50-1b 98 85 f8 f6 b0 94 5f   G....Q7P......._
    0050 - 40 d3 bf fb 8f 25 91 6f-b9 56 01 3a 36 3f 12 5e   @....%.o.V.:6?.^
    0060 - 04 18 e1 dd 5b 0e c6 65-dc 4d d2 e2 b7 28 53 c0   ....[..e.M...(S.
    0070 - 44 18 1a 07 67 a0 28 1d-8f 59 42 dd 3f 3f b2 cc   D...g.(..YB.??..
    0080 - 9a 07 fd fd 11 77 9c de-20 81 72 ca ce 72 aa e1   .....w.. .r..r..
    0090 - bb 88 b8 43 95 45 9f 92-63 7c 5d b9 91 d7 dc fc   ...C.E..c|].....
    00a0 - 46 09 11 5a e3 e2 47 8c-6c a2 33 cd ea d3 eb 8e   F..Z..G.l.3.....
    00b0 - 93 31 d9 4f 50 b6 8e f6-18 52 a3 00 ec 46 ea f3   .1.OP....R...F..
    00c0 - d9 90 c7 13 66 c8 0d 48-33 f0 95 d2 23 a4 d4 fe   ....f..H3...#...

    Start Time: 1708369270
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 76600B12BC59EAD5F5C4F0DC4841EDC7E3678A6CF15E63E5F9C5C003DB2C1458
    Session-ID-ctx: 
    Resumption PSK: 6B359D1E0E7AF130D784DD8DEA295299D1B15313A6DDAB4A361A2938E771C4D982C355A42ED760BCA0ADC07A38C4F0A6
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - dc 1b 67 7e 6b 49 ec f9-e1 0a 8a 6e cb ac b4 e6   ..g~kI.....n....
    0010 - 81 4d 28 c7 24 06 82 53-e3 31 e7 e3 83 e6 21 32   .M(.$..S.1....!2
    0020 - 22 fb fc ab e8 fd ab 8b-76 d6 f5 96 fd 20 c8 de   ".......v.... ..
    0030 - b3 15 b1 11 a9 82 ac f4-f7 85 03 35 d7 2e ab d9   ...........5....
    0040 - ad 31 c6 b1 d7 33 42 21-24 ea 6c 6b 58 a8 52 4f   .1...3B!$.lkX.RO
    0050 - f9 ff f5 b9 ca 8b df be-64 23 59 02 9f 17 2c a6   ........d#Y...,.
    0060 - 49 eb 47 3c c8 62 ba ad-3d aa 6c 28 d5 be 9a a9   I.G<.b..=.l(....
    0070 - e8 08 a0 db a2 19 b0 b2-ea fa 2e af d9 db 3a cf   ..............:.
    0080 - 76 8f 57 a4 b6 e5 ef b4-81 60 d8 7b c0 c4 f1 0b   v.W......`.{....
    0090 - e7 66 49 66 53 87 8f 21-d4 27 bc 19 75 83 79 ab   .fIfS..!.'..u.y.
    00a0 - b7 e8 51 02 af dd 70 a1-b5 14 2a c4 b0 0a 28 25   ..Q...p...*...(%
    00b0 - 22 64 65 10 d1 99 76 3b-55 6b 57 64 c4 53 f3 0f   "de...v;UkWd.S..
    00c0 - 03 26 fa 20 96 2f 04 3c-d6 ce 1f b6 54 64 2f 5a   .&. ./.<....Td/Z

    Start Time: 1708369270
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
bandit15@bandit:~$ 





```

## Notas adicionales


OpenSSL es una biblioteca para la comunicación segura a través de redes. Implementa los protocolos criptográficos Transport Layer Security (TLS) y Secure Sockets Layer (SSL) que se utilizan, por ejemplo, en HTTPS para proteger el tráfico web.

openssl s_client -> es la implementación de un cliente simple que se conecta a un servidor mediante SSL/TLS.

## Referencias 

https://www.openssl.org/docs/man1.0.2/man1/openssl-s_client.html