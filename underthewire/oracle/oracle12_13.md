## Level Goal
The password for oracle13 is the IP of the system that this user has previously established a remote desktop with.

## Solution
My intial approach is to use <code>netstat</code> to find remote client IPs listed in port 3389, which is the port used during a Remote Desktop Protocol (RDP). However, once that approach proves fruitless, I switched to (once again) checking the registry key where IP addresses during RDP are stored, which is <code>HKEY_CURRENT_USER\Software\Microsoft\Terminal Server Client</code>   
```powershell
PS C:\users\oracle12\desktop> netstat -aon | findstr 3389                      
  TCP    0.0.0.0:3389           0.0.0.0:0              LISTENING       264     
  TCP    [::]:3389              [::]:0                 LISTENING       264     
  UDP    0.0.0.0:3389           *:*                                    264     
  UDP    0.0.0.0:63389          *:*                                    2228    
  UDP    [::]:3389              *:*                                    264

PS C:\users\oracle12\desktop> Get-ChildItem Registry::"HKEY_CURRENT_USER\SOFTWAR
E\Microsoft\Terminal Server Client"                                             
                                                                                
                                                                                
    Hive: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Terminal Server Client           
                                                                                
                                                                                
Name                           Property                                         
----                           --------                                         
192.168.2.3                    UsernameHint : MyServer\raccoon

PS C:\users\oracle12\desktop> Get-ChildItem Registry::"HKEY_CURRENT_USER\SOFTWA
RE\Microsoft\Terminal Server Client" -Name                                     
192.168.2.3
```
Notice that only <code>url6</code> is a reference to a <code>.biz</code> site, therefore, we take its name as the password. <br>
<strong>Password:</strong> <code>192.168.2.3</code>
