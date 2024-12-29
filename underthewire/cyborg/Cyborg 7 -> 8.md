## Level Goal
The password for cyborg8 is the executable name of a program that will start automatically when cyborg7 logs in.

## Solution
- Get the <code>Run</code> key from the registry. ([link](https://learn.microsoft.com/en-us/windows/win32/setupapi/run-and-runonce-registry-keys))
```powershell
PS C:\users\cyborg7\desktop> $key = "HKEY_CURRENT_USER\Software\Microsoft\Windows\Curre
ntVersion\"                                                                                  
```
- Investigate the program that automatically starts, meaning its pathname will contain a <code>\Run</code>.
```powershell
PS C:\users\cyborg7\desktop> $(gci $key | ? {$_.name -like '*run*'}).Property          
SKYNET                                                                                 
PS C:\users\cyborg7\desktop> $(gci $key | ? {$_.name -like '*run*'}).Property.toLower()                                                                              
skynet
```
<strong>Password:</strong> <code>skynet</code>
