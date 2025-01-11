## Level Goal
The password for trebek13 is the username of the user who created the user Lor San Tekka as depicted in the event logs on the desktop PLUS the name of the file on the desktop.

## Solution
Use <code>Get-WinEvent</code> and look for <code>Message</code> mentioning the user  Lor San Tekka with the <code>ID</code> 4720, which marks that a user account was created. Looking under the section of <code>Subject</code>, we learn the username of the one who added Lor San Tekka.
```powershell
PS C:\users\trebek12\desktop> ls


    Directory: C:\users\trebek12\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:49 AM              0 53                            
-a----        8/30/2018   5:55 AM       99684352 security.evtx        -
                                               
PS C:\users\trebek12\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.Message
 -like '*lor*san*tekka*' -and $_.id -eq 4720} | select -expandproperty message  
A user account was created.                                                     
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1150  
        Account Name:           poe.dameron                                     
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x1235812                                       
                                                                                
New Account:                                                                    
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1151  
        Account Name:           lor.tekka                                       
        Account Domain:         UNDERTHEWIRE                                    
                                                                                
Attributes:                                                                     
        SAM Account Name:       lor.tekka                                       
        Display Name:           Tekka, Lor San                                  
        User Principal Name:    lor.tekka@underthewire.tech                     
        Home Directory:         -                                               
        Home Drive:             -                                               
        Script Path:            -                                               
        Profile Path:           -                                               
        User Workstations:      -                                               
        Password Last Set:      <never>                                         
        Account Expires:                <never>                                 
        Primary Group ID:       513                                             
        Allowed To Delegate To: -                                               
        Old UAC Value:          0x0                                             
        New UAC Value:          0x15                                            
        User Account Control:                                                   
                Account Disabled                                                
                'Password Not Required' - Enabled                               
                'Normal Account' - Enabled                                      
        User Parameters:        -                                               
        SID History:            -                                               
        Logon Hours:            <value not set>                                 
                                                                                
Additional Information:                                                         
        Privileges              -                                                                                                           
```
<strong>Password:</strong> <code>poe.dameron53</code>
