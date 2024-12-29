## Level Goal
The password for groot5 is the name of the Drax subkey within the HKEY_CURRENT_USER (HKCU) registry hive.

## Solution
This particular challenge was very confusing to me, because I could not look for what a Drax subkey was at all. In the end, I try to list all of the subkeys in the <code>HKCU</code> registry with a filter on the name which has "Drax" in it. The output also generated for some 'Access Denied' notifications, even though I did get the name of the subkey.
Generally, I am still looking for a more elegant solution if possible.
```powershell
PS HKCU:\> Get-ChildItem -Recurse | ? {$_.Name -like "*Drax*"}                    
                                                                                  
                                                                                  
    Hive: HKEY_CURRENT_USER\Software\Microsoft\Assistance                         
                                                                                  
                                                                                  
Name                           Property                                           
----                           --------                                           
Drax                           destroyer : test                                   
                                                                                  
                                                                                  
    Hive: HKEY_CURRENT_USER\Software\Microsoft\Assistance\Drax                    
                                                                                  
                                                                                  
Name                           Property                                           
----                           --------                                           
destroyer                   
```
<strong>Password:</strong> <code>destroyer</code>
