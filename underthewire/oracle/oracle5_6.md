## Level Goal
The password for oracle6 is the name of the GPO that contains a description of “I_AM_GROOT” PLUS the name of the file on the user’s desktop.

## Solution
Use the <code>Get-GPO</code> cmdlet and select objects where the <code>Description</code> parameter is “I_AM_GROOT”.
```powershell
PS C:\users\Oracle5\desktop> Get-GPO -All | ? {$_.Description -eq “I_AM_GROOT”}


DisplayName      : Charlie
DomainName       : underthewire.tech
Owner            : underthewire\Domain Admins
Id               : 44080cf1-1053-467d-b000-2ea3f27dbbfa
GpoStatus        : AllSettingsEnabled
Description      : I_am_Groot
CreationTime     : 11/20/2018 12:18:09 AM
ModificationTime : 11/20/2018 12:18:08 AM
UserVersion      : AD Version: 0, SysVol Version: 0
ComputerVersion  : AD Version: 0, SysVol Version: 0
WmiFilter        : 


PS C:\users\Oracle5\desktop> $($(Get-GPO -All | ? {$_.Description -eq “I_AM_GROO
T”}).DisplayName + $(ls).Name).toLower()                                        
charlie1337                                                             
```
<strong>Password:</strong> <code>charlie1337</code>
