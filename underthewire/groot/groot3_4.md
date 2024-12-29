## Level Goal
The password for groot4 is the number of times the word “beetle” is listed in the file on the desktop.

## Solution
```powershell
PS C:\users\Groot3\desktop> ls           


    Directory: C:\users\Groot3\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018   5:52 AM        2357296 words.txt                     


PS C:\users\Groot3\desktop> $text = $(gc words.txt).split(' ')
PS C:\users\Groot3\desktop> $($text | ? {$_ -eq "beetle"}).count
5
PS C:\users\Groot3\desktop>
```
<strong>Password:</strong> <code>5</code>
