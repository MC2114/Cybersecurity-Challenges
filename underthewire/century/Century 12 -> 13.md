## Level Goal
The password for Century13 is the description of the computer designated as a Domain Controller within this domain PLUS the name of the file on the desktop.

NOTE:
- The password will be lowercase no matter how it appears on the screen.
- If the description "today_is" and the file on the desktop is named "_cool", the password would be "today_is_cool"

## Solution
Use the <code> Get-ADDomainController </code> cmdlet to see all of the Properties associated with the Domain Controllet
```powershell
PS C:\users\century12\desktop> Get-ADDomainController                                  
                                                                                       
                                                                                       
ComputerObjectDN           : CN=UTW,OU=Domain Controllers,DC=underthewire,DC=tech      
DefaultPartition           : DC=underthewire,DC=tech                                   
Domain                     : underthewire.tech                                         
Enabled                    : True                                                      
Forest                     : underthewire.tech                                         
HostName                   : utw.underthewire.tech                                     
InvocationId               : 09ee1897-2210-4ac9-989d-e19b4241e9c6                      
IPv4Address                : 192.99.167.156                                            
IPv6Address                :                                                           
IsGlobalCatalog            : True                                                      
IsReadOnly                 : False                                                     
LdapPort                   : 389                                                       
Name                       : UTW                                                       
NTDSSettingsObjectDN       : CN=NTDS Settings,CN=UTW,CN=Servers,CN=Default-First-Site- 
                             Name,CN=Sites,CN=Configuration,DC=underthewire,DC=tech    
OperatingSystem            : Windows Server 2016 Standard                              
OperatingSystemHotfix      :                                                           
OperatingSystemServicePack :                                                           
OperatingSystemVersion     : 10.0 (14393)                                              
OperationMasterRoles       : {SchemaMaster, DomainNamingMaster, PDCEmulator,           
                             RIDMaster...}                                             
Partitions                 : {DC=ForestDnsZones,DC=underthewire,DC=tech,               
                             DC=DomainDnsZones,DC=underthewire,DC=tech,                
                             CN=Schema,CN=Configuration,DC=underthewire,DC=tech,       
                             CN=Configuration,DC=underthewire,DC=tech...}              
ServerObjectDN             : CN=UTW,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN= 
                             Configuration,DC=underthewire,DC=tech                     
ServerObjectGuid           : df17c8a3-dd76-438b-8ddf-b7ad3e624618                      
Site                       : Default-First-Site-Name                                   
SslPort                    : 636                                                                                                                                                        
```
- We want to use <code>Get-ADComputer</code> to access the Domain Controller.
- Since we learned that the <code>Name</code> is <code>UTW</code>, we can filter the identity by <code>-Identity "UTW"</code>
- Since we specifically want the description of the comupter UTW designated as a DC, we would add the parameter <code>-Properties Description</code>
```powershell
PS C:\users\century12\desktop> $($(Get-ADComputer -Identity "UTW" -Properties Descripti
on).Description + $(ls).name)                                                          
i_authenticate_things
```
<strong>Password:</strong> <code>i_authenticate_things</code>
