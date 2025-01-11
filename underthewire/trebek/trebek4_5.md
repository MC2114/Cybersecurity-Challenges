## Level Goal
The password for trebek5 is the last execution date of Microsoft Access PLUS the name of the text file on the user’s desktop.

## Solution
Per the [hint](https://cloud.google.com/blog/topics/threat-intelligence/execute/) provided, Windows Prefetch sounds like a good place to find evidence of file execution. By default, it stores information for the last 128 executed files in prefetch files found in <code>C:WindowsPrefetch"</code>. It seems that the name of the file executed for Microsoft Access is <code>MSACCESS.EXE-*</code>, so we will pick the date specifically for that one. 
```powershell
PS C:\users\trebek4\desktop> ls


    Directory: C:\users\trebek4\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:46 AM              0 _red    

PS C:\users\trebek4\desktop> gci C:\Windows\Prefetch | findstr /i 'microsoft acc
ess'                                                                            
-a----        8/30/2018   5:54 AM          52138 MICROSOFT.PHOTOS.EXE-31469B2C. 
-a----        8/30/2018   5:54 AM          49569 MICROSOFT.PHOTOS.EXE-C4759B04. 
-a----        8/30/2018   5:54 AM          54941 MICROSOFTEDGE.EXE-6F460926.pf  
-a----        8/30/2018   5:54 AM          49529 MICROSOFTEDGE.EXE-A6A5C345.pf  
-a----         1/5/2017   6:04 PM          65058 MSACCESS.EXE-EF45328A.pf
  
PS C:\users\trebek4\desktop> gci C:\Windows\Prefetch | findstr MSACCESS         
-a----         1/5/2017   6:04 PM          65058 MSACCESS.EXE-EF45328A.pf   
```
<strong>Password:</strong> <code>01/05/2017_red</code>
