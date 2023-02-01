SysInternals Suite

SysInternals

accesschk.exe

Querying Service Configurations for Services

~~~PowerShell
.\accesschk.exe /accepteula -uwcqv <username> <service>
~~~

Checking Permissions on Script Files (i.e. PS1, Bat. Etc.)

~~~PowerShell
.\accesschk.exe /accepteula -quv <USER> <ScriptFile>
~~~

Checking Permissions on a Directory

~~~PowerShell
.\accesschk.exe /accepteula -d  “<FullDirectoryPath>”
~~~

