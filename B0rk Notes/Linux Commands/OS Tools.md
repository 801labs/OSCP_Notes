~~~bash
cat cme.out | grep -a "SMBv1:True" | cut -d ' ' -f 10 > smbv1_hosts.txt
~~~

~~~bash
cat cme.out | grep -a "signing:False" | cut -d ' ' -f 10 > nosigning_hosts.txt
~~~

~~~bash
cat rdp_msf.out | grep -a "NLA: No"
~~~

