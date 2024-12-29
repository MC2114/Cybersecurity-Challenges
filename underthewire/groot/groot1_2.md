## Level Goal
The password for groot2 is the last five alphanumeric characters of the MD5 hash of this system’s hosts file.

## Solution
- Use <code>Get-FileHash</code> to get the MD5 hash of the hosts file.
- Hosts file are generally located in <code>C:\Windows\System32\drive</code>
```powershell
PS C:\users\Groot1\desktop> Get-FileHash -Algorithm MD5 -Path C:\Windows\System32\drive
rs\etc\hosts                                                                           
                                                                                       
Algorithm       Hash                                                                   
---------       ----                                                                   
MD5             6EEC08310BD5328FFC8FB72CD8E464C3

PS C:\users\Groot1\desktop> $hash = $($(Get-FileHash -Algorithm MD5 -Path C:\Windows\Sy
stem32\drivers\etc\hosts).Hash                                                         
>> $hash = $($(Get-FileHash -Algorithm MD5 -Path C:\Windows\System32\drivers\etc\hosts)
.Hash                                                                                  
PS C:\users\Groot1\desktop> ($hash -join '').toLower()                                 
464c3
```
<strong>Password:</strong> <code>464c3</code>
