## Level Goal
The password for cyborg13 is the first four characters of the base64 encoded full path to the file that started the i_heart_robots service PLUS the name of the file on the desktop.

## Solution
Find the full path to the file that started the i_heart_robots service.
```powershell
PS C:\users\cyborg12\desktop> Get-WmiObject win32_service | ? {$_.name -eq "i_heart_rob
ots"}


ExitCode  : 1077
Name      : i_heart_robots
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS C:\users\cyborg12\desktop> $path = $(Get-WmiObject win32_service | ? {$_.name -eq "i
_heart_robots"}).PathName                                                              
PS C:\users\cyborg12\desktop> echo $path                                               
c:\windows\system32\cmd.exe                                                                           
```
Encode the filepath into files for Base64 decoding.
```powershell
$bytes = [System.Text.Encoding]::UTF8.GetBytes($path)                                                                          
```
Decode the file and add the first 4 characters (lowercase) to the name of the file on the desktop.
```powershell
PS C:\users\cyborg12\desktop> [Convert]::ToBase64String($bytes)                        
Yzpcd2luZG93c1xzeXN0ZW0zMlxjbWQuZXhl
PS C:\users\cyborg12\desktop> ls                                                       
                                                                                       
                                                                                       
    Directory: C:\users\cyborg12\desktop                                               
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        8/30/2018  10:45 AM              0 _heart  
```
<strong>Password:</strong> <code>yzpc_heart</code>
