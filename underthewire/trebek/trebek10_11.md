## Level Goal
The password for trebek11 is the last name of the user who enabled Obi-Wan Kenobi’s account as depicted in the event logs on the desktop PLUS the name of the file on the desktop.

## Solution
Once again, we use the <code>Get-WinEvent</code> to look for our target event in th event log (yay!). When we look at the initial message listed, we can see that the event ID 4722 signifies that a new user has been enabled (which is also confirmed through the Appendix). From there, we would want to take a closer look at who authorized this event.
```powershell
PS C:\users\trebek10\desktop> ls                                                
                                                                                
                                                                                
    Directory: C:\users\trebek10\desktop                                        
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:48 AM              0 2121                           
-a----        8/30/2018   5:54 AM       99684352 security.evtx  

PS C:\users\trebek10\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.Message
 -like '*obi-wan*kenobi*'}                                                      
                                                                                
                                                                                
   ProviderName: Microsoft-Windows-Security-Auditing                            
                                                                                
TimeCreated                     Id LevelDisplayName Message                     
-----------                     -- ---------------- -------                     
5/11/2017 6:56:12 PM          4722 Information      A user account was enabl... 
5/11/2017 6:56:12 PM          4738 Information      A user account was chang... 
5/11/2017 6:56:12 PM          4738 Information      A user account was chang... 
5/11/2017 6:56:12 PM          4724 Information      An attempt was made to r... 
5/11/2017 6:56:12 PM          4738 Information      A user account was chang... 
5/11/2017 6:56:12 PM          4720 Information      A user account was creat...

PS C:\users\trebek10\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.Message
 -like '*obi-wan*kenobi*' -and $_.Id -eq 4722} | select -expandproperty message 
A user account was enabled.                                                     
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1153  
        Account Name:           admiral.ackbar                                  
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x12CEFCA                                       
                                                                                
Target Account:                                                                 
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1154  
        Account Name:           obi-wan.kenobi                                  
        Account Domain:         UNDERTHEWIRE                         
```
It is easy to notice that the <code>Account Name: admiral.ackbar</code> was responsible here! And there last name was most likely <code>ackbar</code> (if the formatting of <code>ackbar</code> was anything to go by)!<br>
<strong>Password:</strong> <code>ackbar2121</code>
