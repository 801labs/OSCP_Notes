Scheduled Tasks

Checking Scheduled Tasks

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
schtasks /query /fo LIST /v
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
get-scheduledtasks | where {$_.TaskPath -notlike “\Microsoft*”} | ft TaskName,TaskPath,State
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Checking Permissions on Script Files (i.e. PS1, Bat. Etc.)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.\accesschk.exe /accepteula -quv <USER> <ScriptFile>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
