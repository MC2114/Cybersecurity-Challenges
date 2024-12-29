## Level Goal
The password for groot12 is within an alternate data stream (ADS) somewhere on the desktop.

## Solution
To locate the ADS, we can first look through all of the available streams on the system using the <code>Get-Item</code> cmdlet with the <code>-Stream</code> parameter.
```powershell
PS C:\users\Groot11\desktop> get-item * -stream *


PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\
                TPS_Reports01.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop
PSChildName   : TPS_Reports01.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports01.txt                      
Stream        : :$DATA                                                          
Length        : 30                                                              
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports02.doc::$DATA                                        
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports02.doc::$DATA                                        
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports02.doc                      
Stream        : :$DATA                                                          
Length        : 30                                                              
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports03.txt::$DATA                                        
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports03.txt::$DATA                                        
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports03.txt                      
Stream        : :$DATA                                                          
Length        : 0                                                               
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports04.pdf::$DATA                                        
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports04.pdf::$DATA                                        
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports04.pdf                      
Stream        : :$DATA                                                          
Length        : 30                                                              
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports04.pdf:secret                                        
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports04.pdf:secret                                        
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports04.pdf                      
Stream        : secret                                                          
Length        : 12                                                              
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports05.xlsx::$DATA                                       
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports05.xlsx::$DATA                                       
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports05.xlsx                     
Stream        : :$DATA                                                          
Length        : 30                                                              
                                                                                
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop\ 
                TPS_Reports06.pptx::$DATA                                       
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\users\Groot11\desktop  
PSChildName   : TPS_Reports06.pptx::$DATA                                       
PSDrive       : C                                                               
PSProvider    : Microsoft.PowerShell.Core\FileSystem                            
PSIsContainer : False                                                           
FileName      : C:\users\Groot11\desktop\TPS_Reports06.pptx                     
Stream        : :$DATA                                                          
Length        : 30    
```
We notice that <code>TPS_Reports04.pdf</code> has 2 streams: <code>$DATA</code> and <code>secret</code>. Thus we read the ADS for the <code>TPS_Reports04.pdf</code> file.
```powershell
PS C:\users\Groot11\desktop> get-item TPS_Reports04.pdf -Stream secret | gc     
spaceships                  
```
<strong>Password:</strong> <code>spaceships</code>
