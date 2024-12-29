## Level Goal
The password for cyborg12 is located in the IIS log. The password is not Mozilla or Opera.

## Solution
We know that the IIS log is located somewhere in the directory <code>C:\inetpub\logs\logfiles</code>, so we will find the filepath.
```powershell
PS C:\users\cyborg11\desktop> gci -Path "C:\inetpub\logs" -File -Recurse | where {$_.Na
me -like '*.log'}                                                                      
                                                                                       
                                                                                       
    Directory: C:\inetpub\logs\logfiles\w3svc1                                         
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        8/30/2018   5:52 AM        1099641 u_ex160413.log                                                                           
```
Now that we know that the filepath is <code>C:\inetpub\logs\logfiles\w3svc1\u_ex160413.log</code>, we will select strings with the pattern "password" to find the password.
```powershell
PS C:\users\cyborg11\desktop> cat C:\inetpub\logs\logfiles\w3svc1\u_ex160413.log | sls 
password                                                                               
                                                                                       
2016-04-13 04:14:12 W3SVC1 Century 172.31.45.65 GET / - 80 - 172.31.45.65 HTTP/1.1     
LordHelmet/5.0+(CombTheDesert)+Password+is:spaceballs - - century.underthewire.tech    
200 0 0 925 118 0                                                                          
```
<strong>Password:</strong> <code>spaceballs</code>
