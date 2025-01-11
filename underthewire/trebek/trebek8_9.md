## Level Goal
The password for trebek9 the first 8 bytes of the file located on the desktop. Combine the answer together with NO spaces.


## Solution
<code>Get-Content -Encoding Byte</code> allows us to view the content byte-by-byte, and we only need to see the first 8.  
```powershell
PS C:\users\trebek8\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\trebek8\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018   5:55 AM         221184 Clone_Trooper_data.pdf 

PS C:\users\trebek8\desktop> Get-Content .\Clone_Trooper_data.pdf -Encoding Byte
 -TotalCount 8                                                                  
77                                                                              
90                                                                              
144                                                                             
0                                                                               
3                                                                               
0                                                                               
0                                                                               
0                            
                                                                
```
<strong>Password:</strong> <code>779014403000</code>
