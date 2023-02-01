Proxychains and FoxyProxy

*** PLEASE NOTE THAT THESE ARE TO BE USED WHEN A TUNNEL IS ESTABLISHED ***

Proxychains

Proxychains usage:

~~~bash
proxychains netcat 172.16.0.10 23
~~~

Proxychains config location:

/etc/proxychains.conf

Directory order that proxychains config is checked:

~~~bash
./proxychains.conf
~/.proxychains/proxychains.conf
/etc/proxychains.conf
~~~

Copying Proxychains config to another location:

~~~bash
cp /etc/proxychains.conf .
~~~

When modifying proxychains.conf, the only section to be aware of is at the bottom:

~~~bash
[ProxyList]
~~~

Add the following to the bottom of that:

~~~bash
socks4	127.0.0.1	9050
~~~

Comment out the proxy_dns line as well if scanning is going to be performed through the proxy.

~~~bash
#proxy_dns
~~~

Only TCP Scans will work through Proxychains, UPD will not.

FoxyProxy

Used for Web Proxies and good for quick switching between different web proxies.
