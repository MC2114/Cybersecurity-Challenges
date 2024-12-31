## Level Goal
The password for oracle5 is the name of the GPO that was last created PLUS the name of the file on the user’s desktop.

## Solution
A <code>GPO</code> refers to an Group Policy Object on a Windows system. Using the <code>Get-GPO</code> cmdlet and sorting by <code>CreationTime</code>, which is in chronological order by default, we can pick the last one for get the name for the GPO.
```powershell
PS C:\users\Oracle4\desktop> Get-GPO -All | sort CreationTime | Select -Last 1  
                                                                                
                                                                                
DisplayName      : Alpha                                                        
DomainName       : underthewire.tech                                            
Owner            : underthewire\Domain Admins                                   
Id               : 49401c32-4145-463f-b5e7-816926d4f78d                         
GpoStatus        : AllSettingsEnabled                                           
Description      : Are you there?                                               
CreationTime     : 1/13/2019 9:40:20 PM                                         
ModificationTime : 1/13/2019 9:40:20 PM                                         
UserVersion      : AD Version: 0, SysVol Version: 0                             
ComputerVersion  : AD Version: 0, SysVol Version: 0                             
WmiFilter        :                                                              

                                                                               
PS C:\users\Oracle4\desktop> $($(Get-GPO -All | sort CreationTime | Select -Last
 1).DisplayName + $(ls).name).toLower()                                         
alpha83                                                                                 
```
<strong>Password:</strong> <code>alpha83</code>
