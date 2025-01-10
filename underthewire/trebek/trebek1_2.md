## Level Goal
The password for trebek2 is the name of the script referenced in a deleted task as depicted in the event logs on the desktop.

## Solution
* This challenge is very (uncomfortably) reminiscent of the last few challenges in [Oracle](https://github.com/MC2114/Cybersecurity-Challenges/tree/main/underthewire/oracle). Once again, I use [Appendix L](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor) to look for the the event where a scheduled task was deleted, which happens to be event ID <code>4699.</code>
* Use the cmdlet <code>Verbose</code> and <code>ExpandProperty</code> to emphasize the message and make them easier for investigation. While I knew the script would be located somewhere under the <code>Command</code> section, it was pretty hard to look for the right file and took a bit of trial and error with other files until I got the password. 
```powershell
PS C:\users\trebek1\desktop> Get-WinEvent -Path .\Security.evtx -Verbose | Where
-Object {$_.Id -eq 4699} | Select -ExpandProperty message                       
VERBOSE: Found file c:\users\trebek1\desktop\security.evtx                      
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x338C9                                         
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x74703                                         
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x13069DD                                       
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x12B5275                                       
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x128CC45                                       
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-500   
        Account Name:           Administrator                                   
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x12053FB                                       
                                                                                
Task Information:                                                               
        Task Name:              \Bitvise\Persistent BvSshServer Control Panel\S-
1-5-21-3968311752-1263969649-2303472966-500                                     
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.2" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <LogonTrigger>                                                              
      <Enabled>true</Enabled>                                                   
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
    </LogonTrigger>                                                             
  </Triggers>                                                                   
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <RunLevel>HighestAvailable</RunLevel>                                     
      <UserId>UNDERTHEWIRE\Administrator</UserId>                               
      <LogonType>InteractiveToken</LogonType>                                   
    </Principal>                                                                
  </Principals>                                                                 
  <Settings>                                                                    
    <MultipleInstancesPolicy>Parallel</MultipleInstancesPolicy>                 
    <DisallowStartIfOnBatteries>false</DisallowStartIfOnBatteries>              
    <StopIfGoingOnBatteries>false</StopIfGoingOnBatteries>                      
    <AllowHardTerminate>false</AllowHardTerminate>                              
    <StartWhenAvailable>true</StartWhenAvailable>                               
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>false</AllowStartOnDemand>                              
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT0S</ExecutionTimeLimit>                               
    <Priority>6</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Program Files\Bitvise SSH Server\BssCtrl.exe</Command>        
      <Arguments>-startMinimized</Arguments>                                    
    </Exec>                                                                     
  </Actions>                                                                    
</Task>                                                                         
                                                                                
A scheduled task was deleted.                                                   
                                                                                
Subject:                                                                        
        Security ID:            S-1-5-21-3968311752-1263969649-2303472966-1135  
        Account Name:           trebek1                                         
        Account Domain:         UNDERTHEWIRE                                    
        Logon ID:               0x644A01                                        
                                                                                
Task Information:                                                               
        Task Name:              \cleanup mess                                   
        Task Content:           <?xml version="1.0" encoding="UTF-16"?>         
<Task version="1.3" xmlns="http://schemas.microsoft.com/windows/2004/02/mit/task
">                                                                              
  <RegistrationInfo />                                                          
  <Triggers>                                                                    
    <CalendarTrigger>                                                           
      <StartBoundary>2017-05-10T01:00:00</StartBoundary>                        
      <Enabled>true</Enabled>                                                   
      <RandomDelay>P0DT0H0M0S</RandomDelay>                                     
      <ScheduleByDay>                                                           
        <DaysInterval>1</DaysInterval>                                          
      </ScheduleByDay>                                                          
    </CalendarTrigger>                                                          
  </Triggers>                                                                   
  <Settings>                                                                    
    <MultipleInstancesPolicy>IgnoreNew</MultipleInstancesPolicy>                
    <DisallowStartIfOnBatteries>true</DisallowStartIfOnBatteries>               
    <StopIfGoingOnBatteries>true</StopIfGoingOnBatteries>                       
    <AllowHardTerminate>true</AllowHardTerminate>                               
    <StartWhenAvailable>false</StartWhenAvailable>                              
    <RunOnlyIfNetworkAvailable>false</RunOnlyIfNetworkAvailable>                
    <IdleSettings>                                                              
      <Duration>PT10M</Duration>                                                
      <WaitTimeout>PT1H</WaitTimeout>                                           
      <StopOnIdleEnd>true</StopOnIdleEnd>                                       
      <RestartOnIdle>false</RestartOnIdle>                                      
    </IdleSettings>                                                             
    <AllowStartOnDemand>true</AllowStartOnDemand>                               
    <Enabled>true</Enabled>                                                     
    <Hidden>false</Hidden>                                                      
    <RunOnlyIfIdle>false</RunOnlyIfIdle>                                        
    <DisallowStartOnRemoteAppSession>false</DisallowStartOnRemoteAppSession>    
    <UseUnifiedSchedulingEngine>true</UseUnifiedSchedulingEngine>               
    <WakeToRun>false</WakeToRun>                                                
    <ExecutionTimeLimit>PT72H</ExecutionTimeLimit>                              
    <Priority>7</Priority>                                                      
  </Settings>                                                                   
  <Actions Context="Author">                                                    
    <Exec>                                                                      
      <Command>C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe</Comman
d>                                                                              
      <Arguments>-NonInteractive -NoLogo -NoProfile -File 'c:\users\trebek1\mess
_cleaner.ps1'</Arguments>                                                       
    </Exec>                                                                     
  </Actions>                                                                    
  <Principals>                                                                  
    <Principal id="Author">                                                     
      <UserId>UNDERTHEWIRE\trebek1</UserId>                                     
      <LogonType>InteractiveToken</LogonType>                                   
      <RunLevel>LeastPrivilege</RunLevel>                                       
    </Principal>                                                                
  </Principals>                                                                 
</Task> 
```
Also, this is where I realize that I should <s>stop hating myself by navigating that awful appendix and</s> just filter the <code>WinEvent</code> by the <code>Message</code> instead. The following command outputs the same result as above.
```poweshell
PS C:\users\trebek1\desktop> Get-WinEvent -Path .\Security.evtx -Verbose | Where
-Object {$_.Message -like '*task*delete*'} | Select -ExpandProperty message
```
<strong>Password:</strong> <code>mess_cleaner</code>
