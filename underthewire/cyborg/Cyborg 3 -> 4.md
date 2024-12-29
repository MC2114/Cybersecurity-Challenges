## Level Goal
The password for cyborg4 is the number of users in the Cyborg group within Active Directory PLUS the name of the file on the desktop.

## Solution
- Store the users of the Cyborg group in a variable called <code>users</code> using the <code>Get-ADGroup</code> and <code>Get-ADGroupMember</code> 
- Use the <code>count</code> method to return the total number of users.
- Find the name of the file on the desktop
```powershell
PS C:\users\cyborg3\desktop> $users = $(Get-ADGroup Cyborg | Get-ADGroupMember)
PS C:\users\cyborg3\desktop> $users.count
88
PS C:\users\cyborg3\desktop> ls


    Directory: C:\users\cyborg3\desktop
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        2/26/2022   2:14 PM              0 _objects 
```
<strong>Password:</strong> <code>88_objects</code>
