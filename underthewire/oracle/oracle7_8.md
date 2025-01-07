## Level Goal
The password for oracle8 is the name of the domain that a trust is built with PLUS the name of the file on the user’s desktop.

## Solution
In PowerShell, Active Directory trusts refer to relationships between domains where users from the trusted domains can access and allow for authentication in other domains (trustee). This relationship allow for cross-domain collaboration and file sharing in enterprises. In this particular exercise, we will use the <code>Get-ADTrust</code> cmdlet to retriece information about extisting trusts on the computer.
```powershell
PS C:\users\Oracle7\desktop> Get-ADTrust -Filter *                              
                                                                                
                                                                                
Direction               : Outbound
DisallowTransivity      : True
DistinguishedName       : CN=multiverse,CN=System,DC=underthewire,DC=tech
ForestTransitive        : False
IntraForest             : False
IsTreeParent            : False
IsTreeRoot              : False
Name                    : multiverse
ObjectClass             : trustedDomain
ObjectGUID              : bbfcc0ca-e586-4058-9aef-c6b4a6b32708
SelectiveAuthentication : False
SIDFilteringForestAware : False
SIDFilteringQuarantined : False
Source                  : DC=underthewire,DC=tech
Target                  : multiverse
TGTDelegation           : False
TrustAttributes         : 1
TrustedPolicy           :                                                       
TrustingPolicy          :                                                       
TrustType               : MIT                                                   
UplevelOnly             : False                                                 
UsesAESKeys             : False                                                 
UsesRC4Encryption       : False

PS C:\users\Oracle7\desktop> $($(Get-ADTrust -Filter *).Name + $(ls).Name)      
multiverse111                                                              
```
<strong>Password:</strong> <code>multiverse111</code>
