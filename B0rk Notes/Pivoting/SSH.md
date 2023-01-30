SSH

SSH using key file

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ssh -i <id_rsa> user@10.10.10.10
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SSH port forwarding (Reverse SSH Tunnel)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ssh -L 10000:localhost:10000 user@10.10.10.10
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
