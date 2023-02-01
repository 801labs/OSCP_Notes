dig

Looking up SPF Record

~~~bash
dig +short TXT domain.com
~~~

Looking up DKIM Record

~~~bash
dig dkim._domainkey.domain.com TXT
~~~

Looking up DMARC Record

~~~bash
dig +short TXT _dmarc.domain.com
~~~

