View Network Interfaces

~~~bash
airmon-ng
~~~

Start/Stop airmon

~~~bash
airmon-ng check kill
airmon-ng start wlan0
***Kill off services that need to be stopped***
airmon-ng stop wlan0mon
~~~

Start airodump capture

~~~bash
airodump-ng wlan0mon
***
airodump-ng wlan0mon --band abg --write./file --essid-regex "SSID"
~~~