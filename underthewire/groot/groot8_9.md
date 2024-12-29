## Level Goal
The password for groot9 is the description of the firewall rule blocking MySQL PLUS the name of the file on the desktop.

## Solution
First, I look up Firewall-related commands within the terminal itselt. 
```powershell
PS C:\users\Groot8\desktop> Get-Command *firewall*                              
                                                                                
CommandType     Name                                               Version    S 
                                                                              o 
                                                                              u 
                                                                              r 
                                                                              c 
                                                                              e 
-----------     ----                                               -------    - 
Function        Copy-NetFirewallRule                               2.0.0.0    N 
Function        Disable-NetFirewallRule                            2.0.0.0    N 
Function        Enable-NetFirewallRule                             2.0.0.0    N 
Function        Get-NetFirewallAddressFilter                       2.0.0.0    N 
Function        Get-NetFirewallApplicationFilter                   2.0.0.0    N 
Function        Get-NetFirewallInterfaceFilter                     2.0.0.0    N 
Function        Get-NetFirewallInterfaceTypeFilter                 2.0.0.0    N 
Function        Get-NetFirewallPortFilter                          2.0.0.0    N 
Function        Get-NetFirewallProfile                             2.0.0.0    N 
Function        Get-NetFirewallRule                                2.0.0.0    N 
Function        Get-NetFirewallSecurityFilter                      2.0.0.0    N 
Function        Get-NetFirewallServiceFilter                       2.0.0.0    N 
Function        Get-NetFirewallSetting                             2.0.0.0    N 
Function        New-NetFirewallRule                                2.0.0.0    N 
Function        Remove-NetFirewallRule                             2.0.0.0    N 
Function        Rename-NetFirewallRule                             2.0.0.0    N 
Function        Set-NetFirewallAddressFilter                       2.0.0.0    N 
Function        Set-NetFirewallApplicationFilter                   2.0.0.0    N 
Function        Set-NetFirewallInterfaceFilter                     2.0.0.0    N 
Function        Set-NetFirewallInterfaceTypeFilter                 2.0.0.0    N 
Function        Set-NetFirewallPortFilter                          2.0.0.0    N 
Function        Set-NetFirewallProfile                             2.0.0.0    N 
Function        Set-NetFirewallRule                                2.0.0.0    N 
Function        Set-NetFirewallSecurityFilter                      2.0.0.0    N 
Function        Set-NetFirewallServiceFilter                       2.0.0.0    N 
Function        Set-NetFirewallSetting                             2.0.0.0    N 
Function        Show-NetFirewallRule                               2.0.0.0    N 
Application     Firewall.cpl                                       10.0.14... C                                                                                  
```
Since I know that I would be focusing primarily on the <code>Get</code> cmdlets since the task is involved with retrieving information. Specifically, the <code>Get-NetFirewallRule</code> cmdlet seems to be useful to the challenge. Filtering the information by <code>DisplayName</code>, I get all of its properties, including the <code>Description.</code> 
```powershell
PS C:\users\Groot8\desktop> Get-NetFirewallRule | ? {$_.DisplayName -like '*mysq
l*'}                                                                            
                                                                                
                                                                                
Name                  : {8ce6b97d-5c1d-4347-a7fd-1792feb42355}                  
DisplayName           : MySQL                                                   
Description           : call_me                                                 
DisplayGroup          :                                                         
Group                 :                                                         
Enabled               : True                                                    
Profile               : Any                                                     
Platform              : {}                                                      
Direction             : Inbound                                                 
Action                : Block                                                   
EdgeTraversalPolicy   : Block                                                   
LooseSourceMapping    : False                                                   
LocalOnlyMapping      : False                                                   
Owner                 :                                                         
PrimaryStatus         : OK                                                      
Status                : The rule was parsed successfully from the store.        
                        (65536)                                                 
EnforcementStatus     : NotApplicable                                           
PolicyStoreSource     : PersistentStore                                         
PolicyStoreSourceType : Local

PS C:\users\Groot8\desktop> $($(Get-NetFirewallRule | ? {$_.DisplayName -like '*
mysql*'}).Description + $(ls).name)                                             
call_me_starlord
```
<strong>Password:</strong> <code>call_me_starlord</code>
