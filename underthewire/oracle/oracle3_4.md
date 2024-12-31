## Level Goal
The password for oracle4 is the date that the system logs were last wiped as depicted in the event logs on the desktop.

## Solution
The <code>Event Id 1102</code> indicates that the Windows Security audit log has been cleared, therefore, we will query to get the dates using the cmdlet <code>Get-WinEvent</code> 
```powershell
PS C:\users\Oracle3\desktop> ls


    Directory: C:\users\Oracle3\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018   5:52 AM        1118208 Oracle3_Security.evtx         


PS C:\users\Oracle3\desktop> Get-WinEvent -Path 'Oracle3_Security.evtx' | ? {$_.
Id -eq 1102}


   ProviderName: Microsoft-Windows-Eventlog

TimeCreated                     Id LevelDisplayName Message                    
-----------                     -- ---------------- -------                    
5/9/2017 11:36:05 PM          1102 Information      The audit log was cleare...                                                                          
```
<strong>Password:</strong> <code>05/09/2017</code>
