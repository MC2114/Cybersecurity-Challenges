## Level Goal
The password for oracle2 is the timezone in which this system is set to.

## Solution
After searching for a cmdlet, we use the <code>Get-Timezone</code> cmdlet to find the timezone in which this system is set to.
```powershell
PS C:\users\Oracle1\desktop> get-command *timezone*

CommandType     Name                                               Version    S
                                                                              o
                                                                              u
                                                                              r
                                                                              c
                                                                              e
-----------     ----                                               -------    -
Cmdlet          Get-TimeZone                                       3.1.0.0    M
Cmdlet          Set-TimeZone                                       3.1.0.0    M


PS C:\users\Oracle1\desktop> Get-TimeZone


Id                         : UTC
DisplayName                : (UTC) Coordinated Universal Time
StandardName               : Coordinated Universal Time
DaylightName               : Coordinated Universal Time
BaseUtcOffset              : 00:00:00                                           
SupportsDaylightSavingTime : False

PS C:\users\Oracle1\desktop> $(Get-Timezone).Id.toLower()                       
utc
```
<strong>Password:</strong> <code>utc</code>
