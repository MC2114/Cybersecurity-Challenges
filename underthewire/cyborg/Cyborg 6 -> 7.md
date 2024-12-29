## Level Goal
The password for cyborg7 is the decoded text of the string within the file on the desktop.

## Solution
- First, we check the file <code>cypher.txt</code> on the desktop.
- We notice that the code is encrypted in Base64 string.
```powershell
PS C:\users\cyborg6\desktop> ls


    Directory: C:\users\cyborg6\desktop


Mode                LastWriteTime         Length Name                                 
----                -------------         ------ ----                                 
-a----         2/8/2022  10:47 PM             32 cypher.txt                           


PS C:\users\cyborg6\desktop> cat cypher.txt
YwB5AGIAZQByAGcAZQBkAGQAbwBuAA==                                                                                       
```
- Decode the text using PowerShell Base64 decoding.
```powershell
PS C:\users\cyborg6\desktop> [System.Text.Encoding]::Unicode.GetString([System.Convert]
::FromBase64String($text))                                                             
cybergeddon
```
<strong>Password:</strong> <code>cybergeddon</code>
