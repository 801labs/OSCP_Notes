SSH Tunneling and Port Forwarding

SSH Port Forwarding

SSH port forwarding allows the forwarding of a specific port through a SSH connection

example usage:

~~~bash
ssh -L 8000:172.16.0.10:80 user@172.16.0.5 -fN
~~~

Command Breakdown:

-L - creates the local port that is being used on the attacking machine
8000:172.16.0.10:80 - Localport:RemoteIP:RemotePort
user@172.16.0.5 - useraccount@RemoteIPwithSSHAccess
-fN - -f backgrounds the session and -N only sets up the connection

SSH Tunnelling

SSH Tunnelling allows for all traffic to be forwarded through a specific port on the attacking machine and passed through the victim computer

example usage:

~~~bash
ssh -D 1337 user@172.16.0.5 -fN
~~~

Command Breakdown:

-D - Creates proxy to tunnel traffic through on the local machine
1337 - Local port that the proxy is using
user@172.16.0.5 - useraccount@RemoteIPwithSSHAccess
-fN - -f backgrounds the session and -N only sets up the connection

Reverse SSH Tunnelling

Reverse SSH Tunnelling is the act of initiating the proxy connection from the victim machine to the attacker machine (the opposite of the above commands). For this, a SSH key will need to be generated on the Attacking machine to allow connections to create the proxy.

Steps to create a reverse ssh tunnell are listed below:

Generate Key Pair:

~~~bash
ssh-keygen
~~~

Create the SSH directory and the Authorized_Keys file:

~~~bash
mkdir ~/.ssh && touch ~/.ssh/authorized_keys
~~~

Copy the contents of the .pub file created with ssh-keygen. Edit the authorized_keys file that you created and add the following line before pasting the key in:

~~~bash
command="echo 'This account can only be used for port forwarding'",no-agent-forwarding,no-x11-forwarding,no-pty 
~~~

The final entry should look like this:

![[Pasted image 20230102132319.png]]

There should be no new lines, but the line that prepends the key should have a space after the no-pty

Next, check to see if SSH is running on your attacking machine:

~~~bash
systemctl status ssh
~~~

If it is not running, run the following command:

~~~bash
systemctl start ssh
~~~

Setting up the Reverse SSH Port Forwarding:

You can now use the private key on the victim machine to reverse ssh connect back to the attacker machine with the following command:

~~~bash
ssh -R 8000:172.16.0.10:80 kali@172.16.0.20 -i KEYFILE -fN
~~~

Command Breakdown:

-R - Creates the remote port on the attacker machine
8000:172.16.0.10:80 - AttackerMachineProxyPort:RemoteIP:RemotePort
kali@172.16.0.20 - AttackerUser@AttackerIP
-i KEYFILE - -i Specifies to use a Private Key and the KEYFILE is the keyfile/private key **May need to be chmod 600 on the keyfile for it to function properly
-fN - -f backgrounds the session and -N only sets up the connection

Setting up the Reverse SSH Tunnelling:

You can now use the private key on teh victim machine to reverse ssh connect back to the attacker machine with the following command:

~~~bash
ssh -R 1337 kali@172.16.0.20 -i KEYFILE -fN
~~~

Command Breakdown:

-R - Creates the remote port on the attacker machine
1337 - AttackerMachineProxyPort
kali@172.16.0.20 - AttackerUser@AttackerIP
-i KEYFILE - -i Specifies to use a Private Key and the KEYFILE is the keyfile/private key **May need to be chmod 600 on the keyfile for it to function properly
-fN - -f backgrounds the session and -N only sets up the connection

Cleanup Steps:

Check Processes and grep SSH sessions:

~~~bash
ps aux | grep ssh
~~~

Kill Process corresponding with SSH Session:

~~~bash
kill PID
~~~

