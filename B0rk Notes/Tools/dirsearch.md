dirsearch

Dirsearch Usage

Installation and Usage:

~~~bash
sudo apt install dirsearch
~~~

Example usage of dirsearch:

~~~bash
dirsearch -u http://10.10.10.10 -e php,txt,html -x 400,401,403
~~~

Switch explaination:
   ◇ -u → URL Definition
   ◇ -e → Extensions to attempt to bruteforce
   ◇ -x → Excluded responses (Bad Request, Unauthorized, Forbidden)
