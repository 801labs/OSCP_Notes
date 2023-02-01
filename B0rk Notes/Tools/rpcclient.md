RPCClient

Enumerating Users on a Compromised Machine using a Kerberos Ticket

*Connect to Domain Controller
*Enumerate Users
*Get Password Policy Info
*Get Server Information (Helps Identify Out Of Date OS's)

~~~bash
rpcclient -k <DOMAIN CONTROLLER HOSTNAME/IP>
enumdomusers
getdompwinfo
srvinfo
~~~
