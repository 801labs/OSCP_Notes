Manual Enumeration

Identification of machine, kernel, and architecture information

~~~bash
uname -a

cat /proc/version

cat /etc/issue

cat /etc/lsb-release

lscpu

hostname
~~~

Identification of running services

~~~bash
ps aux
~~~

User Enumeration

~~~bash
whoami

id

sudo -l

cat /etc/passwd

cat /etc/shadow

cat /etc/group

history
~~~

Network Enumeration

~~~bash
ifconfig

ip a

ip route

arp -a

ip neigh

netstat -ano
~~~

