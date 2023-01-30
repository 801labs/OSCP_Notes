1-Spiking

**Spiking is the process of finding a buffer overflow within an application**

Start by connecting to the vulnserver on the victim machine by using Netcat in Kali Linux

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
netcat -vn xxx.xxx.xxx.xxx 9999
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
generic_send_tcp spike.spk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**spike.spk**

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s_readline();
s_string("CMD ");
s_string_variable("0");
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
