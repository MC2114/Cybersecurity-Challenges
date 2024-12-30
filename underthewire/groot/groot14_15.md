## Level Goal
The password for groot15 is the description of the share whose name contains “task” in it PLUS the name of the file on the desktop.

## Solution
Use the <code>Get-SmbShare</code> cmdlet to find the share, filtered by <code>Name</code> which contains “task” in it.
```powershell
PS C:\users\Groot14\desktop> Get-SmbShare | ? {$_.Name -like '*task*'}

Name   ScopeName Path Description     
----   --------- ---- -----------     
Tasker *              scheduled_things                             

PS C:\users\Groot14\desktop> $($(Get-SmbShare | ? {$_.Name -like '*task*'}).Desc
ription + $(ls).Name)                                                           
scheduled_things_8
```
<strong>Password:</strong> <code>scheduled_things_8</code>
