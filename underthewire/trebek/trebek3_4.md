## Level Goal
The password for trebek4 is the IP that the user Yoda last logged in from as depicted in the event logs on the desktop PLUS the name of the text file on the user’s desktop.

## Solution
Once again, we would use the cmdlet <code>Get-WinEvent</code> to find the event log we want. From the initial output based purely on filtering the message, I know that the Event ID (out of the 2 options listed <code>4624</code> and <code>4634</code>) would be <code>4624</code>. 
```powershell
PS C:\users\trebek3\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\trebek3\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:46 AM              0 address                        
-a----        8/30/2018   5:55 AM       99684352 security.evtx    

PS C:\users\trebek3\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.Message 
-like '*logged*Yoda*' -and $_.id -eq 4624} | select -expandproperty  Message    
An account was successfully logged on.                                          
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-18                                        
        Account Name:           TREBEK$                                         
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x3E7                                           
                                                                                
Logon Type:                     10                                              
                                                                                
Impersonation Level:            Impersonation                                   
                                                                                
New Logon:                                                                      
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1155  
        Account Name:           yoda                                            
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0xEEB1C                                         
        Logon GUID:             {00000000-0000-0000-0000-000000000000}          
                                                                                
Process Information:                                                            
        Process ID:             0xf10                                           
        Process Name:           C:\Windows\System32\winlogon.exe                
                                                                                
Network Information:                                                            
        Workstation Name:       TREBEK                                          
        Source Network Address: 10.30.1.18                                      
        Source Port:            0                      
```
Therefore, I filter the events again, choosing only the login and excluding the log-off messages, expanding the <code>Message</code> section for clarity. The output is INCREDIBLY long and would be counter-productive to paste them all here, so I will just include the relevant information where we get the IP address.
```powershell
PS C:\users\trebek3\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.Message 
-like '*logged*Yoda*' -and $_.id -eq 4624} | select -expandproperty  Message    
An account was successfully logged on.                                          
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-18                                        
        Account Name:           TREBEK$                                         
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x3E7                                           
                                                                                
Logon Type:                     10                                              
                                                                                
Impersonation Level:            Impersonation                                   
                                                                                
New Logon:                                                                      
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1155  
        Account Name:           yoda                                            
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0xEEB1C                                         
        Logon GUID:             {00000000-0000-0000-0000-000000000000}          
                                                                                
Process Information:                                                            
        Process ID:             0xf10                                           
        Process Name:           C:\Windows\System32\winlogon.exe                
                                                                                
Network Information:                                                            
        Workstation Name:       TREBEK                                          
        Source Network Address: 10.30.1.18                                      
        Source Port:            0     
```
<strong>Password:</strong> <code>10.30.1.18address</code>
