## Level Goal
The password for trebek3 is the name of the executable associated with the C-3PO service PLUS the name of the file on the user’s desktop.

## Solution
*  My first intuition is to use <code>Get-WmiObject</code>, since we are looking for an executable. And it does work well.
```powershell
PS C:\users\trebek2\desktop> Get-WmiObject Win32_service | ? {$_.Name -like '*c-
3po*'}                                                                          
                                                                                
                                                                                
ExitCode  : 0                                                                   
Name      : C-3PO                                                               
ProcessId : 0                                                                   
StartMode : Auto                                                                
State     : Stopped                                                             
Status    : OK

PS C:\users\trebek2\desktop> $(Get-WmiObject Win32_service | ? {$_.Name -like '*
c-3po*'}).PathName                                                              
g:\star_wars\droid.exe

PS C:\users\trebek2\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\trebek2\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:45 AM              0 823                                                         
```
However, I also learned that the <code>sc.exe qc ServiceName</code> command can display all information about the given ServiceName, which serves as a nice (and faster to type) alternative.
```poweshell
PS C:\users\trebek2\desktop> sc.exe qc C-3PO                                    
[SC] QueryServiceConfig SUCCESS                                                 
                                                                                
SERVICE_NAME: C-3PO                                                             
        TYPE               : 10  WIN32_OWN_PROCESS                              
        START_TYPE         : 2   AUTO_START                                     
        ERROR_CONTROL      : 1   NORMAL                                         
        BINARY_PATH_NAME   : g:\star_wars\droid.exe                             
        LOAD_ORDER_GROUP   :                                                    
        TAG                : 0                                                  
        DISPLAY_NAME       : C-3PO                                              
        DEPENDENCIES       :                                                    
        SERVICE_START_NAME : LocalSystem      
```
<strong>Password:</strong> <code>droid823</code>
