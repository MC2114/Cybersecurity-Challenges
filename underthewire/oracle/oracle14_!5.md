## Level Goal
The password for oracle15 is the name of the user who added the user Bereet to the Galaxy security group as depicted in the event logs on the desktop PLUS the name of the text file on the user’s desktop.

## Solution
* Use <code>ls</code> to check the event logs file on the desktop, which is <code>security.evtx</code>. The name of the text file is <code>2112</code>.
* Refer back to [Appendix L](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor), we can see that the <code>WinEvent</code> for adding member to a security-enabled global group is <code>4728</code>. 
```powershell
PS C:\users\Oracle13\desktop> ls                                               
                                                                               
                                                                               
    Directory: C:\users\Oracle13\desktop                                       
                                                                               
                                                                               
Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018  10:51 AM              0 88                            
-a----        8/30/2018   5:52 AM        2166784 security.evtx  

PS C:\users\Oracle14\desktop> Get-WinEvent -Path .\security.evtx | ? {$_.id -eq 
4728} | select *                                                                
                                                                                
                                                                                
Message              : A member was added to a security-enabled global group.   
                                                                                
                       Subject:                                                 
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1622           
                        Account Name:           nebula                          
                        Account Domain:         UNDERTHEWIRE                    
                        Logon ID:               0xBD8CC7                        
                                                                                
                       Member:                                                  
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1623           
                        Account Name:                                           
                       CN=Bereet,OU=Morag,DC=UNDERTHEWIRE,DC=TECH               
                                                                                
                       Group:                                                   
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1626           
                        Group Name:             Galaxy                          
                        Group Domain:           UNDERTHEWIRE                    
                                                                                
                       Additional Information:                                  
                        Privileges:             -                               
Id                   : 4728                                                     
Version              : 0                                                        
Qualifiers           :                                                          
Level                : 0                                                        
Task                 : 13826                                                    
Opcode               : 0                                                        
Keywords             : -9214364837600034816                                     
RecordId             : 128493                                                   
ProviderName         : Microsoft-Windows-Security-Auditing                      
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                     
LogName              : Security                                                 
ProcessId            : 476                                                      
ThreadId             : 1064                                                     
MachineName          : Oracle.UNDERTHEWIRE.TECH                                 
UserId               :                                                          
TimeCreated          : 5/19/2017 1:19:28 AM                                     
ActivityId           :                                                          
RelatedActivityId    :                                                          
ContainerLog         : c:\users\oracle14\desktop\security.evtx                  
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
                                                                                
Message              : A member was added to a security-enabled global group.   
                                                                                
                       Subject:                                                 
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-500            
                        Account Name:           Administrator                   
                        Account Domain:         UNDERTHEWIRE                    
                        Logon ID:               0xB6B6FE                        
                                                                                
                       Member:                                                  
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1621           
                        Account Name:                                           
                       CN=Gamora,OU=Morag,DC=UNDERTHEWIRE,DC=TECH               
                                                                                
                       Group:                                                   
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-512            
                        Group Name:             Domain Admins                   
                        Group Domain:           UNDERTHEWIRE                    
                                                                                
                       Additional Information:                                  
                        Privileges:             -                               
Id                   : 4728                                                     
Version              : 0                                                        
Qualifiers           :                                                          
Level                : 0                                                        
Task                 : 13826                                                    
Opcode               : 0                                                        
Keywords             : -9214364837600034816                                     
RecordId             : 128340                                                   
ProviderName         : Microsoft-Windows-Security-Auditing                      
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                     
LogName              : Security                                                 
ProcessId            : 476                                                      
ThreadId             : 1064                                                     
MachineName          : Oracle.UNDERTHEWIRE.TECH                                 
UserId               :                                                          
TimeCreated          : 5/19/2017 1:17:11 AM                                     
ActivityId           :                                                          
RelatedActivityId    :                                                          
ContainerLog         : c:\users\oracle14\desktop\security.evtx                  
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
                                                                                
Message              : A member was added to a security-enabled global group.   
                                                                                
                       Subject:                                                 
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-500            
                        Account Name:           Administrator                   
                        Account Domain:         UNDERTHEWIRE                    
                        Logon ID:               0xB6B6FE                        
                                                                                
                       Member:                                                  
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1622           
                        Account Name:                                           
                       CN=Nebula,OU=Morag,DC=UNDERTHEWIRE,DC=TECH               
                                                                                
                       Group:                                                   
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-512            
                        Group Name:             Domain Admins                   
                        Group Domain:           UNDERTHEWIRE                    
                                                                                
                       Additional Information:                                  
                        Privileges:             -                               
Id                   : 4728                                                     
Version              : 0                                                        
Qualifiers           :                                                          
Level                : 0                                                        
Task                 : 13826                                                    
Opcode               : 0                                                        
Keywords             : -9214364837600034816                                     
RecordId             : 128337                                                   
ProviderName         : Microsoft-Windows-Security-Auditing                      
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                     
LogName              : Security                                                 
ProcessId            : 476                                                      
ThreadId             : 1064                                                     
MachineName          : Oracle.UNDERTHEWIRE.TECH                                 
UserId               :                                                          
TimeCreated          : 5/19/2017 1:16:54 AM                                     
ActivityId           :                                                          
RelatedActivityId    :                                                          
ContainerLog         : c:\users\oracle14\desktop\security.evtx                  
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
                                                                                
Message              : A member was added to a security-enabled global group.   
                                                                                
                       Subject:                                                 
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-500            
                        Account Name:           Administrator                   
                        Account Domain:         UNDERTHEWIRE                    
                        Logon ID:               0xB227A7                        
                                                                                
                       Member:                                                  
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1610           
                        Account Name:                                           
                       CN=oracle11,OU=Oracle,DC=UNDERTHEWIRE,DC=TECH            
                                                                                
                       Group:                                                   
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-512            
                        Group Name:             Domain Admins                   
                        Group Domain:           UNDERTHEWIRE                    
                                                                                
                       Additional Information:                                  
                        Privileges:             -                               
Id                   : 4728                                                     
Version              : 0                                                        
Qualifiers           :                                                          
Level                : 0                                                        
Task                 : 13826                                                    
Opcode               : 0                                                        
Keywords             : -9214364837600034816                                     
RecordId             : 127998                                                   
ProviderName         : Microsoft-Windows-Security-Auditing                      
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                     
LogName              : Security                                                 
ProcessId            : 476                                                      
ThreadId             : 1064                                                     
MachineName          : Oracle.UNDERTHEWIRE.TECH                                 
UserId               :                                                          
TimeCreated          : 5/19/2017 1:06:18 AM                                     
ActivityId           :                                                          
RelatedActivityId    :                                                          
ContainerLog         : c:\users\oracle14\desktop\security.evtx                  
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
                                                                                
Message              : A member was added to a security-enabled global group.   
                                                                                
                       Subject:                                                 
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-500            
                        Account Name:           Administrator                   
                        Account Domain:         UNDERTHEWIRE                    
                        Logon ID:               0x768225                        
                                                                                
                       Member:                                                  
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-1611           
                        Account Name:                                           
                       CN=oracle12,OU=Oracle,DC=UNDERTHEWIRE,DC=TECH            
                                                                                
                       Group:                                                   
                        Security ID:                                            
                       S-1-5-21-2268727836-2773903800-2952248001-512            
                        Group Name:             Domain Admins                   
                        Group Domain:           UNDERTHEWIRE                    
                                                                                
                       Additional Information:                                  
                        Privileges:             -                               
Id                   : 4728                                                     
Version              : 0                                                        
Qualifiers           :                                                          
Level                : 0                                                        
Task                 : 13826                                                    
Opcode               : 0                                                        
Keywords             : -9214364837600034816                                     
RecordId             : 127886                                                   
ProviderName         : Microsoft-Windows-Security-Auditing                      
ProviderId           : 54849625-5478-4994-a5ba-3e3b0328c30d                     
LogName              : Security                                                 
ProcessId            : 476                                                      
ThreadId             : 1064                                                     
MachineName          : Oracle.UNDERTHEWIRE.TECH                                 
UserId               :                                                          
TimeCreated          : 5/19/2017 1:04:19 AM                                     
ActivityId           :                                                          
RelatedActivityId    :                                                          
ContainerLog         : c:\users\oracle14\desktop\security.evtx                  
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
Notice that in the section detailing <code>Member</code> with <code>Account Name: CN=Bereet</code>, which is the target member we want to look for, they were added by <code>Account Name: nebula</code>. <br>
<strong>Password:</strong> <code>nebula2112</code>
