## Level Goal
The password for groot14 is the name of the Registered Owner of this system as depicted in the Registry PLUS the name of the file on the desktop.

## Solution
The name of the Registered Owner of this system as depicted in the Registry is stored in <code>HKLM:\SOFTWARE\Microsoft\Windows 
NT\CurrentVersion</code>. Using the <code>Get-ItemProperty</code>, we can retrieve the information of the property "RegisteredOwner."
```powershell
PS C:\users\Groot13\desktop> Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows 
NT\CurrentVersion" -Name "RegisteredOwner"                                      
                                                                                
                                                                                
RegisteredOwner : UTW_Team                                                      
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWA 
                  RE\Microsoft\Windows NT\CurrentVersion                        
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWA 
                  RE\Microsoft\Windows NT                                       
PSChildName     : CurrentVersion                                                
PSDrive         : HKLM                                                          
PSProvider      : Microsoft.PowerShell.Core\Registry                            

PS C:\users\Groot13\desktop> ls


    Directory: C:\users\Groot13\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:51 AM              0 _ned        
```
<strong>Password:</strong> <code>utw_team_ned</code>
