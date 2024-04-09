## Table of contents
* [Turn off screen on lock](#Turn-off-screen-on-lock)
* [Remove unwanted apps](#Remove-unwanted-apps)

## Turn off screen on lock
powershell (admin) :
```
powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE \<time in seconds> 
powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOCONLOCK \<time in seconds>
powercfg.exe /setactive SCHEME_CURRENT
```

_VIDEOIDLE = timeout used when the PC is unlocked_
_VIDEOCONLOCK = timeout used when the PC is at a locked screen_

## Remove unwanted apps
> New Outlook (To continue using Windows Mail), Dev Home...

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
