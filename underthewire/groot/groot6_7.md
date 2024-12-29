## Level Goal
The password for groot7 is the name of the program that is set to start when this user logs in PLUS the name of the file on the desktop.

## Solution
I approached this challenge very similarly to [Cyborg 7 -> 8](https://github.com/MC2114/Cybersecurity-Challenges/blob/main/underthewire/cyborg/Cyborg%207%20-%3E%208.md), in that they both concerns the program that starts when the user logs in.
The only difference is to add the file name on the desktop.
```powershell
PS C:\users\Groot6\desktop> gci HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\ |
 ? {$_.name -like '*run*'}
                                                                                  
                                                                                  
    Hive: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion             
                                                                                  
                                                                                  
Name                           Property                                           
----                           --------                                           
Run                            New Value #1 : {}                                  
                               New Value #2 : {}                                  
                               New Value #3 : 0                                   
                               New Value #4 : {}                                  
                               star-lord    : C:\star-lord.exe
PS C:\users\Groot6\desktop> ls


    Directory: C:\users\Groot6\desktop


Mode                LastWriteTime         Length Name                            
----                -------------         ------ ----                            
-a----        8/21/2020   1:24 PM              0 _rules                            
```
<strong>Password:</strong> <code>star-lord_rules</code>
