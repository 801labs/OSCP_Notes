~~~
cat cme.out | grep -a "SMBv1:True" | cut -d ' ' -f 10 > smbv1_hosts.txt
~~~

~~~
cat cme.out | grep -a "signing:False" | cut -d ' ' -f 10 > nosigning_hosts.txt
~~~

~~~
cat rdp_msf.out | grep -a "NLA: No"
~~~

~~~

~~~

~~~

~~~