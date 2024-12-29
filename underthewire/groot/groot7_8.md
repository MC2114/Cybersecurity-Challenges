## Level Goal
The password for groot8 is the name of the dll, as depicted in the registry, associated with the “applockerfltr” service PLUS the name of the file on the desktop.

## Solution
For this challenge, I first noticed that <code>applockerfltr</code> is a service in the registry. After looing it up, I learned that its information (as with all of the computer's systems) would be stored in <code>HKLM:\SYSTEM\CurrentControlSet\Services\. </code> From there, I filtered the output by name and acquired the DLL name from the property <code>Description.</code>
```powershell
PS C:\users\Groot7\desktop> gci HKLM:\SYSTEM\CurrentControlSet\Services\ | ? {$_
.Name -like '*applockerfltr*'}                                                  
                                                                                
                                                                                
    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services                  
                                                                                
                                                                                
Name                           Property                                         
----                           --------                                         
applockerfltr                  DisplayName     :                                
                               @%systemroot%\system32\srpapi.dll,-102           
                               ErrorControl    : 1                              
                               ImagePath       :                                
                               system32\drivers\applockerfltr.sys               
                               Start           : 3                              
                               Type            : 1                              
                               Description     :                                
                               @%systemroot%\system32\srpapi.dll,-103           
                               DependOnService : {FltMgr, AppID, AppIDSvc}      
                                                                                
                                                                                
PS C:\users\Groot7\desktop> ls                                                  
                                                                                
                                                                                
    Directory: C:\users\Groot7\desktop                                          
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        5/31/2021   5:13 PM              0 _home                                                                                   
```
<strong>Password:</strong> <code>srpapi_home</code>
