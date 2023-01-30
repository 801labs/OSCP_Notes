hashcat

Hashcat Example

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
hashcat.exe -D 2 -m 1800 hashes.txt dictionary_file.txt -O -o decrypted_hashes.txt
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Switches used in example:
   ◇ -D → Specifies device to use for cracking (1 == CPU | 2 == GPU | 3 == Co-Processor)
   ◇ -m → Specifies mode/type of hash being cracked (see hash types examples above)
   ◇ -O → Optimized setting
   ◇ -o → output file created with decrypted hashes

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
hashcat.exe -D 2 -m 0 ..\hash.txt ..\Wordlists\massive_pass_unique.lst -O -o ..\decrypted_hash.txt -r rules\OneRuleToRuleThemAll.rule --debug-mode=1 --debug-file=matched.rule
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
