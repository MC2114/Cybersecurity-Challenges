## Level Goal
The password for Century10 is the 161st word within the file on the desktop.

## Solution
Learn the name of the file on the desktop
```powershell
PS C:\users\century9\desktop> ls


    Directory: C:\users\century9\desktop


Mode                LastWriteTime         Length Name                                 
----                -------------         ------ ----                                 
-a----        8/30/2018   3:34 AM           2131 Word_File.txt                          
```
Use <code>Select-Object -Index 160</code> to find the <strong>161st</strong> word in <code>Word_File.txt</code>
```powershell
PS C:\users\century9\desktop> (gc Word_File.txt) -split ' ' | select-object -index 160 
pierid                                                 
```
<strong>Password:</strong> <code>pierid</code>
