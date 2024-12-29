## Level Goal
The password for groot3 is the word that is made up from the letters in the range of 1,481,110 to 1,481,117 within the file on the desktop.

## Solution

```powershell
PS C:\users\Groot2\desktop> ls


    Directory: C:\users\Groot2\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018   5:52 AM        2357268 elements.txt                  

PS C:\users\Groot2\desktop> $text = (gc elements.txt)
PS C:\users\Groot2\desktop> $text[1481110..1481117] -join ''                    
 hiding
```
<strong>Password:</strong> <code>hiding</code>
