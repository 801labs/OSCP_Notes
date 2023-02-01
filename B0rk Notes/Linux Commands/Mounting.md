Mounting

Show mount points

~~~bash
showmount -e <ip>
~~~

NFS Share Mounting

~~~bash
mount -t nfs 10.10.0.10:/backups /var/backups
~~~

CIFS Share Mounting

~~~bash
mount.cifs //192.168.1.9/storage-photo /mnt/windows-storage -o rw,username=pion,password=my_password

mount -t cifs //10.10.10.100/Replication /mnt/Replication -o username=<username>,password=<password>,domain=active.htb
~~~

