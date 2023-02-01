nmap

~~~bash
nmap -iL target_list.txt -T4 -Pn --top-ports [10 100 1000] --max-retries=2 -oA test.txt
~~~

NMap basics

NMap flags:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }


-i                                                                    --Interactive mode [useful if this is a suid binary ;)]
-sV                                                                   --Attemptd to determine the version of running services
-o                                                                    --Enable OS Detection
-p <x> or -p-                                                         --Port scan for specific ports or port scan all ports
--exclude-ports <port ranges>                                         --Excludes ports/port ranges
-Pn                                                                   --Disable host discovery (ping) and just scan for open ports
-n                                                                    --Does not attempt to resolve DNS
-A                                                                    --Enables OS and version detection, executes in-build scripts for further enumeration
-sC                                                                   --Scan with the default nmap scripts
--script <filename>|<category>|<directory>/|<expression>              --Perform NSE Script Scan using a NSE Script
-v                                                                    --Verbose mode
-sU                                                                   --UDP port scan
-sT                                                                   --TCP port scan
-sS                                                                   --TCP SYN port scan
-6                                                                    --Enable IPv6 Scanning (must specify the IPv6 Address and not a host name or IPv4 Addrress with this flag)
-oN <path/file>                                                       --Normal Output (not grep friendly)
-oX <path/file>                                                       --XML Output
-oG <path/file>                                                       --Grepable output
-oS <path/file>                                                       --Leetspeak output (not very useful and only for 133t haXXorZ)
-T<#>                                                                 --Scan timing (1-5)[1==Slowest-5==Fastest]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
