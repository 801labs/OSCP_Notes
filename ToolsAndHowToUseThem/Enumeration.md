## Network Enumeration ##

#### nmapAutomator ####
[github](https://github.com/21y4d/nmapAutomator)
We should verify that this one isn't banned.

### gobuster ###
[github](https://github.com/OJ/gobuster)

```bash
gobuster dir -u http://$ip -w /wordlist

# Search for php pages 
gobuster dir -u http://$ip -w /wordlist -o gobust_php.out -x php
```


## Web Enumeration  /  Vuln Scanning##
### Nikto ###
[github](https://github.com/sullo/nikto)
```bash
# scan something like 801labs.org
nikto -h <domain> -ssl

# scan a list of IP's
nikto -h targetlist.txt
```

Here's an example of how you would generate a target list:

`nmap -p 80,443 801labs.org -oG 801.txt`

`cat 801.txt | awk '/Up$/{print $2}' >> targetlist.txt`


### Wordlists ###
[Pentest Wordlists](https://github.com/Twibow/Pentest-WordLists)

The `raft*` worlists in `seclists/Discovery/Web-Content/` have proven to be exceptionally useful



