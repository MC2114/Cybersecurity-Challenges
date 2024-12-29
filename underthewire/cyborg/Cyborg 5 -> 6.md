## Level Goal
The password for cyborg6 is the last name of the user who has logon hours set on their account PLUS the name of the file on the desktop.

## Solution
- First, we filter users using <code>Get-ADUser</code> and set the parameter of the <code>logonhours</code> to non-null.
```powershell
PS C:\users\cyborg5\desktop> Get-ADUser -filter * -Properties logonhours | ? {($null -n
e $_.logonhours)}                                                                      
                                                                                       
                                                                                       
DistinguishedName : CN=Administrator,CN=Users,DC=underthewire,DC=tech                  
Enabled           : True                                                               
GivenName         :                                                                    
logonhours        : {255, 255, 255, 255...}                                            
Name              : Administrator                                                      
ObjectClass       : user                                                               
ObjectGUID        : 427058c2-1d57-4e49-a23d-204865b502ae                               
SamAccountName    : Administrator                                                      
SID               : S-1-5-21-758131494-606461608-3556270690-500                        
Surname           :                                                                    
UserPrincipalName :                                                                    
                                                                                       
DistinguishedName : CN=Rowray\, Benny  \ ,OU=T-85,OU=X-Wing,DC=underthewire,DC=tech    
Enabled           : False                                                              
GivenName         : Benny                                                              
logonhours        : {0, 0, 0, 0...}                                                    
Name              : Rowray, Benny                                                      
ObjectClass       : user                                                               
ObjectGUID        : c9aad4f3-3e4f-46b5-84db-2bb7105796dd                               
SamAccountName    : Benny.Rowray                                                       
SID               : S-1-5-21-758131494-606461608-3556270690-1647                       
Surname           : Rowray                                                             
UserPrincipalName : Benny.Rowray    
```
- We notice that there are 2 users who fit the criteria; however, one of them does not have a username.
- We query the users again by setting the parameters of both <code>logonhours</code> and <code>surname</code> to non-null and store it as <code>user</code>.
```powershell
PS C:\users\cyborg5\desktop> $user = $(Get-ADUser -filter * -Properties logonhours | ? 
{($null -ne $_.logonhours) -and ($null -ne $_.surname)})
PS C:\users\cyborg5\desktop> $($user.Surname + $(ls).name).toLower()                   
rowray_timer 
```
<strong>Password:</strong> <code>rowray_timer</code>
