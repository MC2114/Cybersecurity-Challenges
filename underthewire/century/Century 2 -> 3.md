## Level Goal
The password for Century3 is the name of the built-in cmdlet that performs the wget like function within PowerShell PLUS the name of the file on the desktop.

## Solution
We can search on Google for the name of the built-in cmdlet, or alternatively, we can use the command <code>get-alias</code> to get its name.
```powershell
PS C:\users\century2\desktop> get-alias wget                                       
                                                                                   
CommandType     Name                                               Version    Sour 
                                                                              ce   
-----------     ----                                               -------    ---- 
Alias           wget -> Invoke-WebRequest
```
Use <code>ls</code> or <code>Get-ChildItem</code> command to get the name of the file on the Desktop.
```powershell
PS C:\users\century2\desktop> Get-ChildItem


    Directory: C:\users\century2\desktop


Mode                LastWriteTime         Length Name                             
----                -------------         ------ ----                             
-a----        8/30/2018   3:29 AM            693 443         
```
<strong>Password:</strong> <code>invoke-webrequest443</code>
