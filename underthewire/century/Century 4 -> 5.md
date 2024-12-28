## Level Goal
The password for Century5 is the name of the file within a directory on the desktop that has spaces in its name.

## Solution
Use <code>ls</code> twice to find the directory with spaces <code>Can You Open Me.txt</code> and check the name of its file inside.
```powershell
PS C:\users\century4\desktop> ls                                        
                                                                                   
                                                                                   
    Directory: C:\users\century4\desktop                                           
                                                                                   
                                                                                   
Mode                LastWriteTime         Length Name                              
----                -------------         ------ ----                              
d-----       12/27/2024   4:00 PM                Can You Open Me                   
d-----        2/14/2024   2:35 PM                Can You Open Me.txt               
d-----        9/12/2024   7:02 PM                test                              
-a----       10/31/2024   4:10 PM              0 filename. txt                     
-a----        8/22/2024   9:19 PM              0 files.txt                         
-a----        8/30/2024  12:52 AM           1290 output.txt  
PS C:\users\century4\desktop> cd '.\Can You Open Me.txt'                           
PS C:\users\century4\desktop\Can You Open Me.txt> ls                               
                                                                                   
                                                                                   
    Directory: C:\users\century4\desktop\Can You Open Me.txt                       
                                                                                   
                                                                                   
Mode                LastWriteTime         Length Name                              
----                -------------         ------ ----                              
-a----        2/14/2024   2:35 PM             24 34182  
```
Alternatively, use the <code>Get-ChildItem -Recurse</code> to list all of the files in the system and the files within.
```powershell
PS C:\users\century4\desktop> Get-ChildItem -Recurse                               
                                                                                   
                                                                                   
    Directory: C:\users\century4\desktop                                           
                                                                                   
                                                                                   
Mode                LastWriteTime         Length Name                              
----                -------------         ------ ----                              
d-----       12/27/2024   4:00 PM                Can You Open Me                   
d-----        2/14/2024   2:35 PM                Can You Open Me.txt               
d-----        9/12/2024   7:02 PM                test                              
-a----       10/31/2024   4:10 PM              0 filename. txt                     
-a----        8/22/2024   9:19 PM              0 files.txt                         
-a----        8/30/2024  12:52 AM           1290 output.txt 
```
<strong>Password:</strong> <code>34182</code>
