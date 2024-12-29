## Level Goal
The password for groot6 is the name of the workstation that the user with a username of “baby.groot” can log into as depicted in Active Directory PLUS the name of the file on the desktop

## Solution
First, I use <code>Get-ADUser -Properties *</code> to list out all of the properties of ADUser “baby.groot”. I notice that there is a parameter <code>LogonWorkstations</code> which might fit the criteria.
```powershell
PS C:\users\Groot5\desktop> Get-ADUser "baby.groot" -Properties *                 
                                                                                  
                                                                                  
AccountExpirationDate                :                                            
accountExpires                       : 9223372036854775807                        
AccountLockoutTime                   :                                            
AccountNotDelegated                  : False                                      
AllowReversiblePasswordEncryption    : False                                      
AuthenticationPolicy                 : {}                                         
AuthenticationPolicySilo             : {}                                         
BadLogonCount                        : 0                                          
badPasswordTime                      : 0                                          
badPwdCount                          : 0                                          
CannotChangePassword                 : False                                      
CanonicalName                        : underthewire.tech/X-Wing/T-65/Groot        
Certificates                         : {}                                         
City                                 :                                            
CN                                   : Groot                                      
codePage                             : 0                                          
Company                              :                                            
CompoundIdentitySupported            : {}                                         
Country                              :                                            
countryCode                          : 0                                          
Created                              : 8/30/2018 3:28:43 AM                       
createTimeStamp                      : 8/30/2018 3:28:43 AM                       
Deleted                              :                                            
Department                           :                                            
Description                          :                                            
DisplayName                          : Groot                                      
DistinguishedName                    : CN=Groot \                                 
                                       ,OU=T-65,OU=X-Wing,DC=underthewire,DC=tech 
Division                             :                                            
DoesNotRequirePreAuth                : False                                      
dSCorePropagationData                : {1/1/1601 12:00:00 AM}                     
EmailAddress                         : baby.groot@underthewire.tech               
EmployeeID                           :                                            
EmployeeNumber                       :                                            
Enabled                              : False                                      
Fax                                  :                                            
GivenName                            : Baby                                       
HomeDirectory                        :                                            
HomedirRequired                      : False                                      
HomeDrive                            :                                            
HomePage                             :                                            
HomePhone                            :                                            
Initials                             :                                            
instanceType                         : 4                                          
isDeleted                            :                                            
KerberosEncryptionType               : {}                                         
LastBadPasswordAttempt               :                                            
LastKnownParent                      :                                            
lastLogoff                           : 0                                          
lastLogon                            : 0                                          
LastLogonDate                        :                                            
LockedOut                            : False                                      
logonCount                           : 0                                          
LogonWorkstations                    : wk11                                       
mail                                 : baby.groot@underthewire.tech               
Manager                              :                                            
MemberOf                             : {}                                         
MNSLogonAccount                      : False                                      
MobilePhone                          :                                            
Modified                             : 8/30/2018 10:51:10 AM                      
modifyTimeStamp                      : 8/30/2018 10:51:10 AM                      
msDS-User-Account-Control-Computed   : 8388608                                    
Name                                 : Groot                                      
nTSecurityDescriptor                 : System.DirectoryServices.ActiveDirectorySe 
                                       curity                                     
ObjectCategory                       : CN=Person,CN=Schema,CN=Configuration,DC=un 
                                       derthewire,DC=tech                         
ObjectClass                          : user                                       
ObjectGUID                           : c938286d-f672-45b7-97ee-b371f0e39836       
objectSid                            : S-1-5-21-758131494-606461608-3556270690-21 
                                       75                                         
Office                               :                                            
OfficePhone                          :                                            
Organization                         :                                            
OtherName                            :                                            
PasswordExpired                      : True                                       
PasswordLastSet                      :                                            
PasswordNeverExpires                 : False                                      
PasswordNotRequired                  : False                                      
POBox                                :                                            
PostalCode                           :                                            
PrimaryGroup                         : CN=Domain                                  
                                       Users,CN=Users,DC=underthewire,DC=tech     
primaryGroupID                       : 513                                        
PrincipalsAllowedToDelegateToAccount : {}                                         
ProfilePath                          :                                            
ProtectedFromAccidentalDeletion      : False                                      
pwdLastSet                           : 0                                          
SamAccountName                       : baby.groot                                 
sAMAccountType                       : 805306368                                  
ScriptPath                           :                                            
sDRightsEffective                    : 0                                          
ServicePrincipalNames                : {}                                         
SID                                  : S-1-5-21-758131494-606461608-3556270690-21 
                                       75                                         
SIDHistory                           : {}                                         
SmartcardLogonRequired               : False                                      
sn                                   : Groot                                      
State                                :                                            
StreetAddress                        :                                            
Surname                              : Groot                                      
Title                                :                                            
TrustedForDelegation                 : False                                      
TrustedToAuthForDelegation           : False                                      
UseDESKeyOnly                        : False                                      
userAccountControl                   : 514                                        
userCertificate                      : {}                                         
UserPrincipalName                    : baby.groot                                 
userWorkstations                     : wk11                                       
uSNChanged                           : 20021                                      
uSNCreated                           : 19663                                      
whenChanged                          : 8/30/2018 10:51:10 AM                      
whenCreated                          : 8/30/2018 3:28:43 AM  s                            
```
Print the solution.
```powershell
PS C:\users\Groot5\desktop> $($(Get-ADUser "baby.groot" -Properties *).LogonWorkst
ations + $(ls).name)                                                              
wk11_enterprise                           
```
<strong>Password:</strong> <code>wk11_enterprise</code>
