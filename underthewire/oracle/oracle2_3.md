## Level Goal
The password for oracle3 is the last five digits of the MD5 hash, from the hashes of files on the desktop that appears twice.

## Solution
First, we want to investigate all of the MD5 hashes (stored into an array as <code>$hashes</code> to find any duplicate values. By filtering <code>Where-Object</code> with the parameter <code>Count</code>being greater than 1, meaning that the hash has appeared at least twice, we can obtain the duplicate hash and extract its final 5 characters.
```powershell
PS C:\users\Oracle2\desktop> Get-FileHash -Algorithm MD5 *                      
                                                                                
Algorithm       Hash                                                            
---------       ----                                                            
MD5             5BE11FF0037EED156F77213658C2F5C4                                
MD5             4CEB4AAE0231B53834280CC5314FB932                                
MD5             226F590B023BF532FBEEB46154288644                                
MD5             1463397F8FDB4B99CDE3DB0B1E37EA6E                                
MD5             F0483A1F2E8A20412DBBFC12F99C1193                                
MD5             FAB743AE9D2C15F5B84975A891133CCB                                
MD5             BA5DACAC4B8791D0A10C606C7DCCD10C                                
MD5             1C579B4F21EB236E0CC7ABBB0313AE4C                                
MD5             5BE11FF0037EED156F77213658C2F5C4                                
MD5             FD74053193C5E5984E905FBDAD1D61BF                                
MD5             3E00A2BF4B49C7D18DBA79DD39C4B19C                                
MD5             0E848B375C2871DBFE0AD405B58BF4E2                                
MD5             4A22F5027B6E3C09C9743DB955B6878A                                
MD5             41E65125606DE228B94CC2C97B401C1A                                
MD5             1E0054A7A7C6D8C820C7307F94513E50                                
MD5             C6DDC40861E16E60E924C34ED00F787B                                
MD5             FEB6246F13187BFBCA82EB9105B04B61                                
MD5             67CE823F3BCC2BCA22ADEB066160CF54                                
MD5             3705066150D7BF296F1E0F0EDC0DB9FA                                
MD5             3444EAB3BB3F80522031104151DAADA5                                
MD5             39A77E07A13922A8C971EB0BEEFFCEE3                                
MD5             CABBDEAF260BF1FE922A8605D4DDD2BE                                
                                                                                
PS C:\users\Oracle2\desktop> $hashes = @(Get-FileHash -Algorithm MD5 *).Hash    
PS C:\users\Oracle2\desktop> $duplicate = $hashes | Group-Object | Where-Object 
{$_.Count -gt 1}                                                                
PS C:\users\Oracle2\desktop> $duplicate                                         
                                                                                
Count Name                      Group                                           
----- ----                      -----                                           
    2 5BE11FF0037EED156F7721... {5BE11FF0037EED156F77213658C2F5C4, 5BE11FF00... 
                                                                                
                                                                                
PS C:\users\Oracle2\desktop> $duplicate = $hashes | Group-Object | Where-Object 
{$_.Count -gt 1} Select-Object -ExpandProperty Name
PS C:\users\Oracle2\desktop> $duplicate = $hashes | Group-Object | Where-Object 
{$_.Count -gt 1} | Select-Object -ExpandProperty Name                           
PS C:\users\Oracle2\desktop> $duplicate                                         
5BE11FF0037EED156F77213658C2F5C4                                                
PS C:\users\Oracle2\desktop> $($duplicate[-5..-1] -join '').toLower()           
2f5c4                                                                                                        
```
<strong>Password:</strong> <code>2f5c4</code>
