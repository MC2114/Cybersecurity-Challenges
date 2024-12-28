## Level Goal
The password for Century11 is the 10th and 8th word of the Windows Update service description combined PLUS the name of the file on the desktop.

## Solution
- Use the <code>Get-Service</code> cmdlet to retrieve the service object with the parameter <code>-Name "wuauserv"</code> for Windows Update service.
- <code>Select-Object -Property *</code> lists out all of the properties of the Windows Update service

```powershell
PS C:\users\century10\desktop> Get-Service -Name "wuauserv" | Select-Object -Property *
                                                                                       
                                                                                       
                                                                                       
Name                : wuauserv                                                         
RequiredServices    : {rpcss}                                                          
CanPauseAndContinue : False                                                            
CanShutdown         : False                                                            
CanStop             : False                                                            
DisplayName         : Windows Update                                                   
DependentServices   : {}                                                               
MachineName         : .                                                                
ServiceName         : wuauserv                                                         
ServicesDependedOn  : {rpcss}                                                          
ServiceHandle       :                                                                  
Status              : Stopped                                                          
ServiceType         : Win32ShareProcess                                                
StartType           : Manual                                                           
Site                :                                                                  
Container           :                           
```
- Use the <code>Get-WmiObject win32_Service -Filter "DisplayName = 'Windows Update'"</code> cmdlet to access the Windows Update information, then use <code>.Description</code> to filter the text.
- Store the text into a variable called <code>$description</code> to easily access its 10th and 8th word.
```powershell
PS C:\users\century10\desktop> $description = $(Get-WmiObject win32_Service -Filter "Di
splayName = 'Windows Update'" | Select-Object -Property Description).Description       
PS C:\users\century10\desktop> echo $description                                       
Enables the detection, download, and installation of updates for Windows and other prog
rams. If this service is disabled, users of this computer will not be able to use Windo
ws Update or its automatic updating feature, and programs will not be able to use the W
indows Update Agent (WUA) API.                                                                                                                          
```
- Checking the text file, we noticed that the text can be parsed using <code>.split(" ")</code>, since each word is singly spaced.
- Use <code>.toLower()</code> to return the password in all lowercase.
```powershell
PS C:\users\century10\desktop> $($($description.split(" "))[9] + $($description.split("
 "))[7] + $(ls).Name)                                                                  
Windowsupdates110                                                                      
PS C:\users\century10\desktop> $($($description.split(" "))[9] + $($description.split("
 "))[7] + $(ls).Name).toLower()                                                        
windowsupdates110
```
<strong>Password:</strong> <code>windowsupdates110</code>
