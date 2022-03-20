# Get All WiFi Passwords Script
One line command/script that shows you all the Wi-Fi networks you have been connected to and their passwords.

```
@echo off && netsh wlan export profile key=clear > nul && findstr /c:"<keyMaterial>" *.xml > WiFi.txt && powershell -Command "(gc WiFi.txt) -replace '<keyMaterial>', '' -replace '</keyMaterial>', '' -replace 'Wi-Fi-', '' -replace '.xml:', ':' | Out-File -encoding ASCII WiFi.txt" && del /f /s /q *.xml > nul && start WiFi.txt && @echo on
```
