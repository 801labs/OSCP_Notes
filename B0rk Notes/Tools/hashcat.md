hashcat

Hashcat Example

~~~cmd
hashcat.exe -D 2 -m 1800 hashes.txt dictionary_file.txt -O -o decrypted_hashes.txt
~~~

Switches used in example:
   ◇ -D → Specifies device to use for cracking (1 == CPU | 2 == GPU | 3 == Co-Processor)
   ◇ -m → Specifies mode/type of hash being cracked (see hash types examples above)
   ◇ -O → Optimized setting
   ◇ -o → output file created with decrypted hashes

~~~cmd
hashcat.exe -m 0 ..\hash.txt ..\Wordlists\rockyou2021.txt -O -o ..\decrypted_hash.txt -r rules\cyclone_250.rule --debug-mode=1 --debug-file=matched.rule
~~~

