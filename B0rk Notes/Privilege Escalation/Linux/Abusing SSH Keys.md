Abusing SSH Keys

authorized_keys vs id_rsa

authorized_keys = public key
id_rsa = private key

Locating SSH Keys

~~~bash
find / -name id_rsa 2> /dev/null

find / -name authorized_keys 2> /dev/null
~~~

When stealing id_rsa you will need to modify the permissions on the attacker copy before being able to use the id_rsa to connect to the server

~~~bash
nano id_rsa

#Paste id_rsa contents to this file and save

chmod 600 id_rsa

ssh -i id_rsa id_rsa-user@xxx.xxx.xxx.xxx
~~~

Creating your own Authorized Key Pairs for accessing a server without password usage

Open PuttyGen and Generate the RSA KeyPair (or if you have an id_rsa key, you can generate the public key)
      ▪ Also note that you should comment this with the user that you would like to have this keypair assigned to i.e. id_rsa-user@xxx.xxx.xxx.xxx
      ▪ Key Passphrase is optional, but should be added if you experience issues

Save the public key as “authorized_keys” (with no file extension)

Save the private key as “id_rsa” (with no file extension)

![[Pasted image 20230102132046.png]]

![[Pasted image 20230102132055.png]]

![[Pasted image 20230102132103.png]]

Now you can place the authorized_keys file on the server that you are accessing in the .ssh folder under the user that you wish to have access to and connect via the same method as shown above using the “ssh -i id_rsa id_rsa-user@xxx.xxx.xxx.xxx” command
