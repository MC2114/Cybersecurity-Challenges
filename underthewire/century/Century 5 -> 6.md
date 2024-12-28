## Level Goal
The password for Century6 is the short name of the domain in which this system resides in PLUS the name of the file on the desktop.

NOTE:
- If the short name of the domain is "blob" and the file on the desktop is named "1234", the password would be "blob1234".
- The password will be lowercase no matter how it appears on the screen.

## Solution
Use <code>Get-ADDomain</code> command to get the information about the Domain of this system. By combining the names of both the domain and the name of the file, we get the password.
```powershell
PS C:\users\century5\desktop> $($(Get-ADDomain).Name + $(ls).Name)                 
underthewire3347 
```
<strong>Password:</strong> <code>underthewire3347</code>
