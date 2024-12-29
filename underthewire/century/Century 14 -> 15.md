## Level Goal
The password for Century14 is the number of words within the file on the desktop.	

## Solution
Use <code>ls</code> command to see the name of the file on the desktop.
```powershell
PS C:\users\century14\desktop> ls


    Directory: C:\users\century14\desktop


Mode                LastWriteTime         Length Name                                 
----                -------------         ------ ----                                 
-a----        8/30/2018  11:24 PM         202900 countpolos                            
```
- Store the content of the file <code>countpolos</code> as a variable called <code>$text</code>
- Filter strings with "polo" using <code>? {$_ -eq "polo"})</code>
```powershell
PS C:\users\century14\desktop> $text = $(gc countpolos).split(' ')
PS C:\users\century14\desktop> $($text | ? {$_ -eq "polo"}).count
153                           
```
<strong>Password:</strong> <code>153</code>
