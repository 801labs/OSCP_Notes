Scheduled Tasks

Checking Scheduled Tasks

~~~cmd
schtasks /query /fo LIST /v
~~~

~~~PowerShell
get-scheduledtasks | where {$_.TaskPath -notlike “\Microsoft*”} | ft TaskName,TaskPath,State
~~~

Checking Permissions on Script Files (i.e. PS1, Bat. Etc.)

~~~PowerShell
.\accesschk.exe /accepteula -quv <USER> <ScriptFile>
~~~

