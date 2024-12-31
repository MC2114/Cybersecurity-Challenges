## Level Goal
The password for oracle7 is the name of the OU that doesn’t have a GPO linked to it PLUS the name of the file on the user’s desktop.

## Solution
Use the <code>Get-ADOrganizationalUnit</code> cmdlet and filter out OUs where the property <code>LinkedGroupPolicyObjects</code> is not set to <code>$null.</code> Initially, I approach this challenge by selecting the OUs where the <code>LinkedGroupPolicyObjects</code> is set to <code>$null.</code> Surprisingly, it did not filter out any OUs (maybe because the <code>$null</code> variable works differently for empty arrays in Powershell). 
```powershell
PS C:\users\Oracle6\desktop> Get-ADOrganizationalUnit -Filter * -Properties Link
edGroupPolicyObjects | ? {!($_.LinkedGroupPolicyObjects -ne @($null))}          
                                                                                
                                                                                
City                     :                                                      
Country                  :                                                      
DistinguishedName        : OU=T-50,OU=X-Wing,DC=underthewire,DC=tech            
LinkedGroupPolicyObjects : {}                                                   
ManagedBy                :                                                      
Name                     : T-50                                                 
ObjectClass              : organizationalUnit                                   
ObjectGUID               : 5ace8bef-c00e-4f58-a543-3fd45436f1d4                 
PostalCode               :                                                      
State                    :                                                      
StreetAddress            :

City                     :                                                      
Country                  :                                                      
DistinguishedName        : OU=Groups,DC=underthewire,DC=tech                    
LinkedGroupPolicyObjects : {}                                                   
ManagedBy                :                                                      
Name                     : Groups                                               
ObjectClass              : organizationalUnit                                   
ObjectGUID               : bf366f71-f291-43ca-8334-cdb18890e332                 
PostalCode               :                                                      
State                    :                                                      
StreetAddress            :

PS C:\users\Oracle6\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\Oracle6\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:50 AM              0 _97                                                              
```
<strong>Password:</strong> <code>t-50_97</code>
