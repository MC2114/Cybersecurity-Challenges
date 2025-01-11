## Level Goal
The password for trebek10 is the name of the potentially rogue share on the system PLUS the name of the file on the desktop.

## Solution
This challenge is very similar to [Groot 14](https://github.com/MC2114/Cybersecurity-Challenges/blob/main/underthewire/groot/groot14_15.md), wehre we use <code>Get-SmbShare</code> (or alternatively, <code>Get-WmiObject -Class Win32_Share</code>  to look at all of the shares on the machine. 
```powershell
PS C:\users\trebek9\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\trebek9\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:48 AM              0 _hiding

PS C:\users\trebek9\desktop> Get-SmbShare                                       
                                                                                
Name           ScopeName Path Description                                       
----           --------- ---- -----------                                       
ADMIN$         *              Remote Admin                                      
C$             *              Default share                                     
IPC$           *              Remote IPC                                        
NETLOGON       *              Logon server share                                
shoretroopers$ *              Nothing to see here                               
SYSVOL         *              Logon server share                                
Tasker         *              scheduled_things                                  
                                                                                
                                                                                
PS C:\users\trebek9\desktop> Get-WmiObject -Class Win32_Share                   
                                                                                
Name           Path Description                                                 
----           ---- -----------                                                 
ADMIN$              Remote Admin                                                
C$                  Default share                                               
IPC$                Remote IPC                                                  
NETLOGON            Logon server share                                          
shoretroopers$      Nothing to see here                                         
SYSVOL              Logon server share                                          
Tasker              scheduled_things                      
                                                                
```
Since we can see that the Description for <code>shoretroopers$</code> is a bit... suspicious, we can deduce that it is the potential rogue file we are looking for. <br>
<strong>Password:</strong> <code>shoretroopers$_hiding</code>
