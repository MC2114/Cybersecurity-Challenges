## Level Goal
The password for groot10 is the name of the OU that doesn’t have accidental deletion protection enabled PLUS the name of the file on the desktop.

## Solution
<code>OU</code> refers to the <strong>Organizational Units</strong> in Active Directories. The general approach, therefore, is to use the cmdlet <code>Get-ADOrganizationalUnit</code> and look for OUs where the <code>ProtectedFromAccidentalDeletion</code> are disabled, or set to false.
```powershell
PS C:\users\Groot9\desktop> Get-ADOrganizationalUnit -filter * -property * | ? {
$_.ProtectedFromAccidentalDeletion -eq $false}


CanonicalName                   : underthewire.tech/X-Wing/T-25
City                            : 
CN                              : 
Country                         : 
Created                         : 8/30/2018 3:21:13 AM
createTimeStamp                 : 8/30/2018 3:21:13 AM
Deleted                         :                                               
Description                     :                                               
DisplayName                     :                                               
DistinguishedName               : OU=T-25,OU=X-Wing,DC=underthewire,DC=tech     
dSCorePropagationData           : {1/1/1601 12:00:00 AM}                        
gPLink                          : [LDAP://cn={49401C32-4145-463F-B5E7-816926D4F 
                                  78D},cn=policies,cn=system,DC=underthewire,DC 
                                  =tech;0]                                      
instanceType                    : 4                                             
isDeleted                       :                                               
LastKnownParent                 :                                               
LinkedGroupPolicyObjects        : {cn={49401C32-4145-463F-B5E7-816926D4F78D},cn 
                                  =policies,cn=system,DC=underthewire,DC=tech}  
ManagedBy                       :                                               
Modified                        : 1/13/2019 9:40:43 PM                          
modifyTimeStamp                 : 1/13/2019 9:40:43 PM                          
Name                            : T-25                                          
nTSecurityDescriptor            : System.DirectoryServices.ActiveDirectorySecur 
                                  ity                                           
ObjectCategory                  : CN=Organizational-Unit,CN=Schema,CN=Configura 
                                  tion,DC=underthewire,DC=tech                  
ObjectClass                     : organizationalUnit                            
ObjectGUID                      : fc15c303-dd9a-4c44-a941-314cc6fdd394          
ou                              : {T-25}                                        
PostalCode                      :                                               
ProtectedFromAccidentalDeletion : False                                         
sDRightsEffective               : 0                                             
State                           :                                               
StreetAddress                   :                                               
uSNChanged                      : 61518                                         
uSNCreated                      : 13668                                         
whenChanged                     : 1/13/2019 9:40:43 PM                          
whenCreated                     : 8/30/2018 3:21:13 AM

PS C:\users\Groot9\desktop> $ou = $(Get-ADOrganizationalUnit -filter * -property
 * | ? { $_.ProtectedFromAccidentalDeletion -eq $false}).Name                                                                                               
PS C:\users\Groot9\desktop> $($ou + $(ls).name).toLower()                                    
t-25_tester
```
<strong>Password:</strong> <code>t-25_tester</code>
