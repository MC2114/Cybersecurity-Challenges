## Level Goal
The password for Century4 is the number of files on the desktop.	

## Solution
Use <code>.Count</code> to tally the number of files on the desktop.
```powershell
PS C:\users\century3\desktop> $(ls).Count
123
```
Alternatively, use the <code>Measure-Object</code> command.
```powershell
PS C:\users\century3\desktop> ls | Measure-Object                                  
                                                                                   
                                                                                   
Count    : 123                                                                     
Average  :                                                                         
Sum      :                                                                         
Maximum  :                                                                         
Minimum  :                                                                         
Property : 
```
<strong>Password:</strong> <code>123</code>
