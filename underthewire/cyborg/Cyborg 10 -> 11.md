## Level Goal
The password for cyborg11 is the description of the Applocker Executable deny policy for ill_be_back.exe PLUS the name of the file on the desktop.

## Solution
Use the <code>Get-AppLockerPolicy</code> cmdlet.
```powershell
PS C:\users\cyborg10\desktop> $($(Get-AppLockerPolicy -Effective).RuleCollections.Descr
iption) + $(ls).name                                                                   
terminated!99                                                                         
```
<strong>Password:</strong> <code>terminated!99</code>
