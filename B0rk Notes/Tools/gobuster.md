gobuster

HTTPS

~~~bash
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -l -t 30 -e -k -x html,.asp,.aspx,.php,.txt,.exe,.bin,.jsp -u https://$1:$port
~~~

HTTP

~~~bash
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -l -t 30 -e -k -x html,.asp,.aspx,.php,.txt,.exe,.bin,.jsp -u http://$1:$port
~~~

