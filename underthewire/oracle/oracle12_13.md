## Level Goal
The password for oracle13 is the IP of the system that this user has previously established a remote desktop with.

## Solution
Use the cmdlet <code>Get-SmbMapping</code> here to retrieve the Server Message Block (SMB) client directory mappings created for a server. Then, by checking its <code>LocalPath</code>, we get the name of the single-letter drive.
```powershell
PS C:\users\Oracle11\desktop> Get-SmbMapping

Status      Local Path Remote Path            
------      ---------- -----------            
Unavailable M:         \\127.0.0.1\WsusContent


PS C:\users\Oracle11\desktop> (Get-SmbMapping).LocalPath
M:

PS C:\users\Oracle11\desktop> ((Get-SmbMapping).LocalPath -split ":")[0].toLower
()                                                                              
m                                                                                                                                                                                    
```
Notice that only <code>url6</code> is a reference to a <code>.biz</code> site, therefore, we take its name as the password. <br>
<strong>Password:</strong> <code>m</code>
