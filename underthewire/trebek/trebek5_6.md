## Level Goal
The password for trebek6 is the name of the executable that is starting at 3/23/2017 8:08:53 PM via the Software Protection service as depicted in the event log on the desktop.

## Solution
For this level, we can simply use <code>Get-WinEvent</code> to retrieve the message at <code>TimeCreated: 3/23/2017 8:08:53 PM</code>, then extend the message on Software Protection.
```powershell
PS C:\users\trebek5\desktop> ls


    Directory: C:\users\trebek5\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018   5:55 AM        5312512 application.evtx              


PS C:\users\trebek5\desktop> Get-WinEvent -Path .\application.evtx | ?{$_.TimeCr
eated -eq '3/23/2017 8:08:53 PM'}


   ProviderName: Microsoft-Windows-Security-SPP

TimeCreated                     Id LevelDisplayName Message                    
-----------                     -- ---------------- -------                    
3/23/2017 8:08:53 PM           900 Information      The Software Protection ...

PS C:\users\trebek5\desktop> Get-WinEvent -Path .\application.evtx | ?{$_.TimeCreated -eq '3/23/2017 8:08:53 PM'} | select -expandproperty message                      
The Software Protection service is starting.
Parameters:caller=wlms.exe   
```
<strong>Password:</strong> <code>wlms</code>
