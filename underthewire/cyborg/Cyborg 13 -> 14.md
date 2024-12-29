## Level Goal
The password cyborg14 is the number of days the refresh interval is set to for DNS aging for the underthewire.tech zone PLUS the name of the file on the desktop.

## Solution
Use the cmdlet <code>Get-DnsServerZoneAging</code> to retrieve information about the refresh interval set to for DNS aging.
```powershell
PS C:\users\cyborg13\desktop> Get-DnsServerZoneAging -Name underthewire.tech 


ZoneName             : underthewire.tech
AgingEnabled         : True
AvailForScavengeTime : 9/21/2018 10:00:00 AM
RefreshInterval      : 22.00:00:00                                                     
NoRefreshInterval    : 7.00:00:00                                                      
ScavengeServers      :                                                                 
                                                                                       
                                                                                       
                                                                                       
PS C:\users\cyborg13\desktop> ls                                                       
                                                                                       
                                                                                       
    Directory: C:\users\cyborg13\desktop                                               
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        8/30/2018  10:45 AM              0 _days

PS C:\users\cyborg13\desktop> $($($(Get-DnsServerZoneAging -Name underthewire.tech).Ref
reshInterval).ToString().Split(".")[0] + $(ls).name)                                   
22_days                                                                     
```
<strong>Password:</strong> <code>22_days</code>
