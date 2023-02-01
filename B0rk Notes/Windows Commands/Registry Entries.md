Registry Entries

~~~cmd
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v KeyName /t REG_SZ /d "DATA" /f
~~~

REG ADD - Add Registry Entry
HKLM\\... - Path to the Registry Key Entry to be Added
/v KeyName - Registry Entry Name
/t REG_SZ - Rigistry Entry Type
/d "DATA" - Data Eepresented by the Registry Entry
/f - Force Without Confirmation (Allows for Automatic Overwriting)