## Level Goal
The password for cyborg9 is the Internet zone that the picture on the desktop was downloaded from.

## Solution
- Check the name of the picture file on the desktop.
- Use <code>-Stream Zone.Identifier</code> to learn the Internet zone of the picture.
```powershell
PS C:\users\cyborg8\desktop> ls                                                        
                                                                                       
                                                                                       
    Directory: C:\users\cyborg8\desktop                                                
                                                                                       
                                                                                       
Mode                LastWriteTime         Length Name                                  
----                -------------         ------ ----                                  
-a----        8/30/2018  10:45 AM          60113 1_qs5nwlcl7f_-SwNlQvOrAw.png
PS C:\users\cyborg8\desktop> gc 1_qs5nwlcl7f_-SwNlQvOrAw.png -Stream Zone.Identifier   
[ZoneTransfer]                                                                         
ZoneId=4                                                                            
```
<strong>Password:</strong> <code>4</code>
