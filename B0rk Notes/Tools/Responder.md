Responder

~~~bash
sudo responder -I tun0
sudo responder -I eth0 -dwF
~~~

Location of Responder Logs for finding Hashes

/usr/share/responder/logs/

~~~bash
cat /usr/share/responder/logs/*.txt | sort -u -t: -k1,2
~~~

Location of Responder Config

/usr/share/responder/Responder.conf