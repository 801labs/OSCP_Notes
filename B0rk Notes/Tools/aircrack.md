View Network Interfaces

~~~
airmon-ng
~~~

Start/Stop airmon

~~~
airmon-ng check kill
airmon-ng start wlan0
***Kill off services that need to be stopped***
airmon-ng stop wlan0mon
~~~

Start airodump capture

~~~
airodump-ng wlan0mon
***
airodump-ng wlan0mon --band abg --write./file --essid-regex "SSID"
~~~