## Level Goal
The password for Century12 is the name of the hidden file within the contacts, desktop, documents, downloads, favorites, music, or videos folder in the user’s profile.

NOTE:
– Exclude “desktop.ini”.
– The password will be lowercase no matter how it appears on the screen.

## Solution
- Use the <code>-Hidden</code> parameter to access the hidden file.
- Use the <code>-ne "desktop.ini"</code> parameter to filter out <code>desktop.ini</code>

```powershell
PS C:\users\century11\desktop> $(ls ../ -R -Hidden -File | ? {$_.name -ne "desktop.ini"}).name                          
NTUSER.DAT                                                                             
ntuser.dat.LOG1                                                                        
ntuser.dat.LOG2                                                                        
NTUSER.DAT{0f893ee4-78e5-11e6-90dd-eefb07825ed9}.TM.blf                                
NTUSER.DAT{0f893ee4-78e5-11e6-90dd-eefb07825ed9}.TMContainer00000000000000000001.regtra
ns-ms                                                                                  
NTUSER.DAT{0f893ee4-78e5-11e6-90dd-eefb07825ed9}.TMContainer00000000000000000002.regtra
ns-ms                                                                                  
ntuser.ini                                                                             
UsrClass.dat                                                                           
UsrClass.dat.LOG1                                                                      
UsrClass.dat.LOG2                                                                      
UsrClass.dat{d82669b3-abff-11e8-90ee-e14c26db97e8}.TM.blf                              
UsrClass.dat{d82669b3-abff-11e8-90ee-e14c26db97e8}.TMContainer00000000000000000001.regt
rans-ms                                                                                
UsrClass.dat{d82669b3-abff-11e8-90ee-e14c26db97e8}.TMContainer00000000000000000002.regt
rans-ms                                                                                
secret_sauce                                                                                                                        
```
<strong>Password:</strong> <code>secret_sauce</code>
