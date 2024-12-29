## Level Goal
The password for cyborg10 is the first name of the user with the phone number of 876-5309 listed in Active Directory PLUS the name of the file on the desktop.

## Solution
Filter by <cide>Office Phone</code> to find the user.
```powershell
PS C:\users\cyborg9\desktop> Get-ADUser -Filter {OfficePhone -eq '876-5309'} -Propertie
s GivenName, OfficePhone                                                               
                                                                                       
                                                                                       
DistinguishedName : CN=Garick\, Onita  \ ,OU=T-65,OU=X-Wing,DC=underthewire,DC=tech    
Enabled           : False                                                              
GivenName         : Onita                                                              
Name              : Garick, Onita                                                      
ObjectClass       : user                                                               
ObjectGUID        : 5fc5bb5b-272a-4b70-877a-ed774029e247                               
OfficePhone       : 876-5309                                                           
SamAccountName    : Onita.Garick                                                       
SID               : S-1-5-21-758131494-606461608-3556270690-2124                       
Surname           : Garick                                                             
UserPrincipalName : Onita.Garick

PS C:\users\cyborg9\desktop> $name = $(Get-ADUser -Filter {OfficePhone -eq '876-5309'} 
-Properties GivenName, OfficePhone).GivenName
PS C:\users\cyborg9\desktop> $($name + $(ls).name).toLower()                           
onita99                                                                           
```
<strong>Password:</strong> <code>onita99</code>
