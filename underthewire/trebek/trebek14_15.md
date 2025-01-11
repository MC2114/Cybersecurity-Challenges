## Level Goal
The password for trebek15 is the output from decoding the PowerShell code found in the account properties of the user account from the previous level PLUS the name of the file on the desktop.

## Solution
The PowerShell command encoded in the previous level was <code>agBvAGkAbgBfAHQAaABlAF8AcgBlAGIAZQBsAHMA</code>. We can easily decode this from Base64 to UTF-8.
```powershell
PS C:\users\trebek14\desktop> ls


    Directory: C:\users\trebek14\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:49 AM              0 _today

PS C:\users\trebek14\desktop> [System.Text.Encoding]::UTF8.GetString([System.Con
vert]::FromBase64String('agBvAGkAbgBfAHQAaABlAF8AcgBlAGIAZQBsAHMA'))            
j o i n _ t h e _ r e b e l s                                                                                                           
```
Very ominous message, and a great way to conclude this challenge as well! This was a lot of fun!
<strong>Password:</strong> <code>join_the_rebels_today</code>
