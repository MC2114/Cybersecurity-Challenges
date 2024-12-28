## Level Goal
The password for Century9 is the number of unique entries within the file on the desktop.	

## Solution
Learn the name of the file on the desktop
```powershell
PS C:\users\century8\desktop> ls


    Directory: C:\users\century8\desktop


Mode                LastWriteTime         Length Name                                 
----                -------------         ------ ----                                  
-a----        8/30/2018   3:33 AM          15858 unique.txt                        
```
Use <code>Select-Object -unique</code> to find all the unique entries within <code>unique.txt</code>
```powershell
PS C:\users\century8\desktop> $(gc unique.txt | select-object -unique).count           
696                         
```
<strong>Password:</strong> <code>696</code>
