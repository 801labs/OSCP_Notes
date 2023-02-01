Searching for Other Networks

Places to search for other networks:

Windows:

~~~cmd
C:\Windows\System32\drivers\etc\hosts
~~~

~~~cmd
arp -a
~~~

~~~cmd
ipconfig /all
~~~

Linux:

~~~bash
arp -a
~~~

~~~bash
/etc/hosts
~~~

~~~bash
/etc/resolv.conf
~~~

~~~bash
nmcli dev show
~~~

Ping Sweep of Another Network (BASH):

~~~bash
for i in {1..255}; do (ping -c 1 192.168.1.${i} | grep "bytes from" &); done
~~~

Port Scanning of another Network (BASH):

~~~bash
for i in {1..65535}; do (echo > /dev/tcp/192.168.1.1/$i) >/dev/null 2>&1 && echo $i is open; done
~~~

