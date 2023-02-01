Checking for Domain Join

TDB Dump

~~~bash
tdbdump /var/lib/samba/private/secrets.tdb
~~~

If the machine is domain joined it will have the domain name in the dump in the hostname. (ex. host/ubuntu.els.local@ELS.LOCAL)

If Samba 3 is employed, the password will be in plaintext. If Samba 4 is employed it will be in a hex value that can be decoded.

Requesting a Kerberos Ticket

~~~bash
kinit machinename@domain
~~~

Listing Active Kerberos Tickets

~~~bash
klist
~~~

Finding Domain Controllers

~~~bash
cat /etc/krb5.conf
~~~

