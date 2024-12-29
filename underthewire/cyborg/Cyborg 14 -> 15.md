## Level Goal
The password for cyborg15 is the caption for the DCOM application setting for application ID {59B8AFA0-229E-46D9-B980-DDA2C817EC7E} PLUS the name of the file on the desktop.

## Solution
- Use <code>Get-WmiObject -Class "Win32_DCOMApplication"</code> cmdlet.
- Filter by <code>AppID</code>
```powershell
PS C:\users\cyborg14\desktop> (Get-WmiObject -Class "Win32_DCOMApplication" | ? AppID -
eq '{59B8AFA0-229E-46D9-B980-DDA2C817EC7E}').Caption                                   
propshts                                                                               
PS C:\users\cyborg14\desktop> ls                                                       
                                                                                       
                                                                                       
    Directory: C:\users\cyborg14\desktop                                               
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        8/30/2018  10:45 AM              0 _objects   
```
<strong>Password:</strong> <code>propshts_objects</code>
