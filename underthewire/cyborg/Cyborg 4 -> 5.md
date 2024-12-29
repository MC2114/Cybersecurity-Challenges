## Level Goal
The password for cyborg5 is the PowerShell module name with a version number of 8.9.8.9 PLUS the name of the file on the desktop.

## Solution
- First, we use <code>Get-Module -ListAvailable</code> to see all of the PowerShell modules available on the computer. We notice that it is categorized by <code>ModuleType</code>, <code>Version</code>, <code>Name</code> and <code>ExportedCommands</code> 
```powershell
PS C:\users\cyborg4\desktop> Get-Module -ListAvailable


    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands            
---------- -------    ----                                ----------------            
Script     1.0.1      Microsoft.PowerShell.Operation.V... {Get-OperationValidation,...
Binary     1.0.0.1    PackageManagement                   {Find-Package, Get-Packag...
Script     3.4.0      Pester                              {Describe, Context, It, S...
Script     1.0.0.1    PowerShellGet                       {Install-Module, Find-Mod...
Script     1.2        PSReadline                          {Get-PSReadlineKeyHandler...
Script     1.0.6      PSSlack                             {Find-SlackMessage, Get-P...
Script     1.0.0      PSSlack                             {Find-SlackMessage, Get-P...
Script     0.1.3      PSSlack                             {Find-SlackMessage, Get-P...
Script     0.1.0      PSSlack                             {Find-SlackMessage, Get-P...

 
```
- Filter it by Version 8.9.8.9
- Concatenate the string found with the name of the file on the desktop
```powershell
PS C:\users\cyborg4\desktop> Get-Module -ListAvailable | ? Version -eq "8.9.8.9"       
                                                                                       
                                                                                       
    Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules                      
                                                                                       
                                                                                       
ModuleType Version    Name                                ExportedCommands             
---------- -------    ----                                ----------------             
Manifest   8.9.8.9    bacon                               Get-bacon                    
                                                                                       
                                                                                       
PS C:\users\cyborg4\desktop> $mod = $(Get-Module -ListAvailable | ? Version -eq "8.9.8.9").Name
PS C:\users\cyborg4\desktop> $($mod + $(ls).name)                                      
bacon_eggs                 
```
<strong>Password:</strong> <code>bacon_eggs</code>
