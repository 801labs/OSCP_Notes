Service Takeover

Stopping and Starting Services

~~~PowerShell
sc stop <servicename>
sc start <servicename>
~~~

Querying Service Configurations

~~~PowerShell
sc qc <servicename>
~~~

Querying Service States

~~~PowerShell
sc query <servicename>
~~~

Querying Service Configurations for Services

~~~PowerShell
.\accesschk.exe /accepteula -uwcqv <username> <service>
~~~

