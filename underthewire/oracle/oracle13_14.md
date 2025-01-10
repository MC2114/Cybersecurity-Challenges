## Level Goal
The password for oracle14 is the name of the user who created the Galaxy security group as depicted in the event logs on the desktop PLUS the name of the text file on the user’s desktop.

## Solution
* Use <code>ls</code> to check the event logs file on the desktop, which is <code>security.evtx</code>
* Use the <code>Get-WinEvent</code> cmdlet to retrieve the message containing the user information. Initially, I tried to filter the security group by <code>-LogName Security</code>, but this raises an error message. So, I change to filtering by the event <code>ID: 4727</code> instead. On Windows, Event ID 4727 signifies that a security-enabled global group was created.
* For future reference, the table for all Win Events ID is [here](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor).
* The name of the text file is <code>88</code>
```powershell
PS C:\users\Oracle13\desktop> ls                                               
                                                                               
                                                                               
    Directory: C:\users\Oracle13\desktop                                       
                                                                               
                                                                               
Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:51 AM              0 88                            
-a----        8/30/2018   5:52 AM        2166784 security.evtx  

PS C:\users\Oracle13\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.id -eq
 4727} | select *                                                              
                                                                               
                                                                               
Message              : A security-enabled global group was created.            
                                                                               
                       Subject:                                                
                        Security ID:                                           
                       S-1-5-21-2268727836-2773903800-2952248001-1621          
                        Account Name:           gamora                         
                        Account Domain:         UNDERTHEWIRE                   
                        Logon ID:               0xBC24FF                       
                                                                               
                       New Group:                                              
                        Security ID:                                           
                       S-1-5-21-2268727836-2773903800-2952248001-1626          
                        Group Name:             Galaxy                         
                        Group Domain:           UNDERTHEWIRE                   
                                                                               
                       Attributes:                                             
                        SAM Account Name:       Galaxy                         
                        SID History:            -                              
                                                                               
                       Additional Information:                                 
                        Privileges:             -                              
Id                   : 4727                                                    
Version              : 0                                                       
Qualifiers           :                                                         
Level                : 0                                                       
Task                 : 13826                                                   
Opcode               : 0                                                       
Keywords             : -9214364837600034816                                    
RecordId             : 128424                                                  
ProviderName         : Microsoft-Windows-Security-Auditing                     
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                    
LogName              : Security                                                
ProcessId            : 476                                                     
ThreadId             : 1064                                                    
MachineName          : Oracle.UNDERTHEWIRE.TECH                                
UserId               :                                                         
TimeCreated          : 5/19/2017 1:18:26 AM                                    
ActivityId           :                                                         
RelatedActivityId    :                                                         
ContainerLog         : c:\users\oracle13\desktop\security.evtx                 
MatchedQueryIds      : {}                                                      
Bookmark             : System.Diagnostics.Eventing.Reader.EventBookmark        
LevelDisplayName     : Information                                             
OpcodeDisplayName    : Info                                                    
TaskDisplayName      : Security Group Management                               
KeywordsDisplayNames : {Audit Success}                                         
Properties           : {System.Diagnostics.Eventing.Reader.EventProperty,      
                       System.Diagnostics.Eventing.Reader.EventProperty,       
                       System.Diagnostics.Eventing.Reader.EventProperty,       
                       System.Diagnostics.Eventing.Reader.EventProperty...}    
                                                                               
Message              : A security-enabled global group was created.            
                                                                               
                       Subject:                                                
                        Security ID:                                           
                       S-1-5-21-2268727836-2773903800-2952248001-500           
                        Account Name:           Administrator                  
                        Account Domain:         UNDERTHEWIRE                   
                        Logon ID:               0xB6B6FE                       
                                                                               
                       New Group:                                              
                        Security ID:                                           
                       S-1-5-21-2268727836-2773903800-2952248001-1625          
                        Group Name:             Guardian                       
                        Group Domain:           UNDERTHEWIRE                   
                                                                               
                       Attributes:                                             
                        SAM Account Name:       Guardian                       
                        SID History:            -                              
                                                                               
                       Additional Information:                                 
                        Privileges:             -                              
Id                   : 4727                                                    
Version              : 0                                                       
Qualifiers           :                                                         
Level                : 0                                                       
Task                 : 13826                                                   
Opcode               : 0                                                       
Keywords             : -9214364837600034816                                    
RecordId             : 128328                                                  
ProviderName         : Microsoft-Windows-Security-Auditing                     
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                    
LogName              : Security                                                
ProcessId            : 476                                                     
ThreadId             : 1064                                                    
MachineName          : Oracle.UNDERTHEWIRE.TECH                                
UserId               :                                                         
TimeCreated          : 5/19/2017 1:16:17 AM                                    
ActivityId           :                                                         
RelatedActivityId    :                                                         
ContainerLog         : c:\users\oracle13\desktop\security.evtx                 
MatchedQueryIds      : {}                                                      
Bookmark             : System.Diagnostics.Eventing.Reader.EventBookmark        
LevelDisplayName     : Information                                             
OpcodeDisplayName    : Info                                                    
TaskDisplayName      : Security Group Management                               
KeywordsDisplayNames : {Audit Success}                                         
Properties           : {System.Diagnostics.Eventing.Reader.EventProperty,      
                       System.Diagnostics.Eventing.Reader.EventProperty,       
                       System.Diagnostics.Eventing.Reader.EventProperty,       
                       System.Diagnostics.Eventing.Reader.EventProperty...}    
                                                                               
                                                           
```
Notice that in the message with <code>Group Name: Galaxy</code>, it also says <code>Account Name: gamora</code>. <br>
<strong>Password:</strong> <code>gamora88</code>
