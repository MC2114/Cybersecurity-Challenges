## Level Goal
The password for Century14 is the number of words within the file on the desktop.	

## Solution
Use <code>ls</code> command to see the name of the file on the desktop.
```powershell
PS C:\users\century13\desktop> ls


    Directory: C:\users\century13\desktop


Mode                LastWriteTime         Length Name                                 
----                -------------         ------ ----                                 
-a----        8/30/2018   3:38 AM           7894 countmywords                            
```
Store the content of the file <code>countmywords</code> as a variable called <code>$text</code>, then use <code>.count</code> to count the number of words after the text has been splitted using spaces.
```powershell
PS C:\users\century13\desktop> $text = $(gc countmywords)                              
PS C:\users\century13\desktop> ($text.split(' ')).count                                
755                          
```
<strong>Password:</strong> <code>755</code>
