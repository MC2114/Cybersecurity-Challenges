## Level Goal
The password for trebek12 is the username of the user who was created on 11 May 17 at 26 minutes after the hour, as depicted in the event logs on the desktop PLUS the name of the file on the desktop.

## Solution
Use <code>Get-WinEvent</code> and filter the result by <code>TimeCreated</code> and <code>ID</code> 4720, which marks that a user account was created. Looking under the section of <code>New Account</code>, we learn the name of the user who was created.
```powershell
PS C:\users\trebek11\desktop> ls                                                
                                                                                
                                                                                
    Directory: C:\users\trebek11\desktop                                        
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:49 AM              0 100                            
-a----        8/30/2018   5:55 AM       99684352 security.evtx    

PS C:\users\trebek11\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.TimeCre
ated -like '*5/11/2017*:26:*' -and $_.id -eq 4720}                              
                                                                                
                                                                                
   ProviderName: Microsoft-Windows-Security-Auditing                            
                                                                                
TimeCreated                     Id LevelDisplayName Message                     
-----------                     -- ---------------- -------                     
5/11/2017 6:26:08 PM          4720 Information      A user account was creat...
PS C:\users\trebek11\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.TimeCre
ated -like '*5/11/2017*:26:*' -and $_.id -eq 4720} | select -expandproperty mess
age                                                                             
A user account was created.                                                     
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1150  
        Account Name:           poe.dameron                                     
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x1235812                                       
                                                                                
New Account:                                                                    
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1152  
        Account Name:           general.hux                                     
        Account Domain:         UNDERTHEWIRE                                    
                                                                                
Attributes:                                                                     
        SAM Account Name:       general.hux                                     
        Display Name:           Hux, General                                    
        User Principal Name:    general.hux@underthewire.tech                   
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
<strong>Password:</strong> <code>general.hux100</code>
