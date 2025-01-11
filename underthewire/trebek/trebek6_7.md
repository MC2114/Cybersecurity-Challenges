## Level Goal
The password for trebek7 is the total number of DLLs within the “C:\program files\adobe\” folder and it’s subfolders PLUS the name of the file on the desktop.

## Solution
A <code>DLL</code> file, which stands for **"Dynamic Link Library,"** is a type of computer file on Windows systems that contains code and data that can be shared and used by multiple programs simultaneously. We can easily obtain thu number of <code>.dll</code> files by recursively count all the files in the <code>C:\program files\adobe\ </code> directory.  
```powershell
PS C:\users\trebek6\desktop> $count = $(gci -r -Path “C:\program files\adobe\” | fin
dstr dll).count                                                                     
PS C:\users\trebek6\desktop> $count                                                 
40

PS C:\users\trebek6\desktop> ls                                                     
                                                                                    
                                                                                    
    Directory: C:\users\trebek6\desktop                                             
                                                                                    
                                                                                    
Mode                LastWriteTime         Length Name                               
----                -------------         ------ ----                               
-a----        8/30/2018  10:47 AM              0 _reader    
```
<strong>Password:</strong> <code>40_reader</code>
