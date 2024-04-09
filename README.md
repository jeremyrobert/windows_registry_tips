## Turn off the screen when locked
powershell (admin) :
```
powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE \<time in seconds> 
powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOCONLOCK \<time in seconds>
powercfg.exe /setactive SCHEME_CURRENT
```

_VIDEOIDLE = timeout used when the PC is unlocked_
_VIDEOCONLOCK = timeout used when the PC is at a locked screen_

## Remove and disable automatic installation of Outlook and Dev Home
> To continue using Windows Mail
> 
Remove apps via powershell (admin) :
```
Get-AppxProvisionedPackage -Online | where Displayname -match 'devhome|outlook' | Remove-AppxProvisionedPackage -AllUsers -Online
```

Delete this keys in regedit :
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Orchestrator\UScheduler\DevHomeUpdate]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Orchestrator\UScheduler\OutlookUpdate]
```
and
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\Orchestrator\UScheduler_Oobe\DevHomeUpdate]
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\Orchestrator\UScheduler_Oobe\OutlookUpdate]
```
