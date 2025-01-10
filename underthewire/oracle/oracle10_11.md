## Level Goal
The password for oracle11 is the .biz site the user has previously navigated to.

## Solution
A <code>.biz</code> site is a website that uses the <code>.biz</code> domain extension, which is a generic top-level domain (gTLD) for businesses. Thanks to the hint given <em>("Registry is awesome!")</em>, we know to once again investigate the root PowerShell registry keys, specifically the <code>HKCU</code> drive since it stores all information related to the user currently logged on, including browser activities. Thus, we check the Registry Key <code>TypedURLs</code> located in the <code>HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\TypedURLs</code> to investigate the URLs visited by the last user.  
```powershell
PS C:\users\Oracle10\desktop> Get-ItemProperty Registry::"HKEY_CURRENT_USER\Soft
ware\Microsoft\Internet Explorer\TypedURLs"                                     
                                                                                
                                                                                
url1         : http://go.microsoft.com/fwlink/p/?LinkId=255141                  
url2         : http://google.com                                                
url3         : http://underthewire.tech                                         
url4         : http://bimmerfest.com                                            
url5         : http://nba.com                                                   
url6         : http://yondu.biz                                                 
url7         : http://hardknocks.edu                                            
url8         : http://installation.org                                          
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER\Software\M 
               icrosoft\Internet Explorer\TypedURLs                             
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER\Software\M 
               icrosoft\Internet Explorer                                       
PSChildName  : TypedURLs                                                        
PSProvider   : Microsoft.PowerShell.Core\Registry                                                                                                                                                           
```
Notice that only <code>url6</code> is a reference to a <code>.biz</code> site, therefore, we take its name as the password. <br>
<strong>Password:</strong> <code>yondu</code>
