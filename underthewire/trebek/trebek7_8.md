## Level Goal
The password for trebek8 is the name of the program set to run prior to login if sticky keys are activated PLUS the name of the file on the desktop.

## Solution
* Fun fact: A quick search online gave me the name of the executable set to run prior to login if sticky keys are activated (which is <code>sethc.exe</code>). It was thanks to that information that I know where to look amongst all of the executables in the registry.
* Per the hint given, we learn that we can find the executable (and its debugger) in the registry key <code>HKLM\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options</code>. 
```powershell
PS C:\users\trebek7\desktop> gci Registry::"HKLM\Software\Microsoft\Windows NT\C
urrentVersion\Image File Execution Options"


    Hive: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Image File 
    Execution Options


Name                           Property                                        
----                           --------                                         
chrome.exe                     MaxLoaderThreads : 1                             
cscript.exe                    DisableExceptionChainValidation : 3              
dllhost.exe                    DisableExceptionChainValidation : 3              
DllNXOptions                   Apitrap.dll         : 1                          
                               ASSTE.dll           : 1                          
                               AVSTE.dll           : 1                          
                               Cleanup.dll         : 1                          
                               divx.dll            : 1                          
                               divxdec.ax          : 1                          
                               DJSMAR00.dll        : 1                          
                               DRMINST.dll         : 1                          
                               eMigrationmmc.dll   : 1                          
                               EncryptPatchVer.dll : 1                          
                               eProcedureMMC.dll   : 1                          
                               eQueryMMC.dll       : 1                          
                               fullsoft.dll        : 1                          
                               ISSTE.dll           : 1                          
                               javai.dll           : 1                          
                               jvm.dll             : 1                          
                               jvm_g.dll           : 1                          
                               main123w.dll        : 1                          
                               msci_uno.dll        : 1                          
                               mscoree.dll         : 1                          
                               mscorsvr.dll        : 1                          
                               mscorwks.dll        : 1                          
                               msjava.dll          : 1                          
                               mso.dll             : 1                          
                               NAVOPTRF.dll        : 1                          
                               NPMLIC.dll          : 1                          
                               NSWSTE.dll          : 1                          
                               PMSTE.dll           : 1                          
                               ppw32hlp.dll        : 1                          
                               symlcnet.dll        : 1                          
                               TFDTCTT8.dll        : 1                          
                               udtapi.dll          : 1                          
                               ums.dll             : 1                          
                               vb40032.dll         : 1                          
                               vbe6.dll            : 1                          
                               Vegas60k.dll        : 1                          
                               xlmlEN.dll          : 1                          
drvinst.exe                    DisableExceptionChainValidation : 3              
ehexthost32.exe                DisableExceptionChainValidation : 3              
explorer.exe                   DisableExceptionChainValidation : 3              
ExtExport.exe                  MitigationOptions : 256                          
ie4uinit.exe                   MitigationOptions : 256                          
ieinstal.exe                   MitigationOptions : 256                          
ielowutil.exe                  MitigationOptions : 256                          
ieUnatt.exe                    MitigationOptions : 256                          
iexplore.exe                   DisableExceptionChainValidation : 0              
                               DisableUserModeCallbackFilter   : 1              
                               MitigationOptions               : 256            
InetMgr.exe                    MitigationOptions : 1152921504606846976          
MiracastView.exe               MitigationOptions : 4294967296                   
mmc.exe                        DisableExceptionChainValidation : 3              
MRT.exe                        CFGOptions : 1                                   
mscorsvw.exe                   MitigationOptions : 4294967296                   
msfeedssync.exe                MitigationOptions : 256                          
mshta.exe                      MitigationOptions : 256                          
MsMpEng.exe                    CFGOptions : 1                                   
ngen.exe                       MitigationOptions : 4294967296                   
ngentask.exe                   MitigationOptions : 4294967296                   
PresentationHost.exe           MitigationOptions : 1118481                      
PrintDialog.exe                MitigationOptions : 4294967296                   
rundll32.exe                   DisableExceptionChainValidation : 3              
runtimebroker.exe              MitigationOptions : 4294967296                   
searchprotocolhost.exe         DisableExceptionChainValidation : 3              
sethc.exe                      Debugger : han_solo.exe                                                 
spoolsv.exe                    DisableExceptionChainValidation : 3              
svchost.exe                    MinimumStackCommitInBytes : 32768                
SystemSettings.exe             MitigationOptions : 4294967296                   
wscript.exe                    DisableExceptionChainValidation : 3

PS C:\users\trebek7\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\trebek7\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:47 AM              0 99                             
                                                                
```
<strong>Password:</strong> <code>han_solo99</code>
