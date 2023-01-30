Responder

~~~
sudo responder -I tun0
sudo responder -I eth0 -dwF
~~~

Location of Responder Logs for finding Hashes

/usr/share/responder/logs/

~~~
cat /usr/share/responder/logs/*.txt | sort -u -t: -k1,2
~~~