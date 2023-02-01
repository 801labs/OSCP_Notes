SMB Client

Listing Directories from port 445

~~~bash
smbclient -L //10.10.10.100
~~~

Using a Kerberos Ticket

~~~bash
smbclient -k -L //10.10.10.100
~~~

Additional Commands when SMBClient is connected

~~~bash
prompt off
~~~

~~~bash
recurse on
~~~

~~~bash
mget *
~~~

