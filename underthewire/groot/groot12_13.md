## Level Goal
The password for groot13 is the owner of the Nine Realms folder on the desktop.

## Solution
Use the <code>Get-Acl</code> cmdlet to get the owner of the folder. Since we want to disregard the Administrator group or any system, the password is only <code>airwolf</code>.
```powershell
PS C:\users\Groot12\desktop> get-acl ".\Nine Realms"


    Directory: C:\users\Groot12\desktop


Path        Owner                Access                                         
----        -----                ------                                         
Nine Realms underthewire\Airwolf NT AUTHORITY\SYSTEM Allow  FullControl...                  
```
<strong>Password:</strong> <code>airwolf</code>
