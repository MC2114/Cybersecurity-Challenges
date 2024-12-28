## Level Goal
The password for Century2 is the build version of the instance of PowerShell installed on this system.

<strong>NOTE:</strong>
- The format is as follows: **.*.*****.****
- Include all periods
- Be sure to look for build version and NOT PowerShell version


<strong>IMPORTANT:</strong>
Once you feel you have completed the Century1 challenge, start a new connection to the server, and log in with the username of Century2 and this password will be the answer from Century1. If successful, close out the Century1 connection and begin to solve the Century2 challenge. This concept is repeated over and over until you reach the end of the game.

## Solution
Use <code>$psversiontable</code> command to get the version of the system.
```powershell
PS C:\users\century1\desktop> $psversiontable

Name                           Value                                              
----                           -----                                              
PSVersion                      5.1.14393.7254                                     
PSEdition                      Desktop                                            
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}                            
BuildVersion                   10.0.14393.7254                                    
CLRVersion                     4.0.30319.42000                                    
WSManStackVersion              3.0                                                 
PSRemotingProtocolVersion      2.3                                                 
SerializationVersion           1.1.0.1  
```
<strong>Password:</strong> <code>10.0.14393.7254</code>
