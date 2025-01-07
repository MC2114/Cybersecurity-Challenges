## Level Goal
The password for oracle10 is the computer name of the DNS record of the mail server listed in the UnderTheWire.tech zone PLUS the name of the file on the user’s desktop.

## Solution
Use the cmdlet <code>Get-DnsServerResourceRecord</code> to retrieve the DNS record needed. From the [Microsoft PowerShell Doumentation](https://learn.microsoft.com/en-us/powershell/module/dnsserver/get-dnsserverresourcerecord?view=windowsserver2025-ps), we learn that we can filter the DNS records by the following parameters: <code>-ZoneName</code> and <code>-RRType</code>. For <code>-ZoneName</code>, the String value is pretty straightforward: "UnderTheWire.tech". However, for <code>-RRType</code>, we have to research a bit to find which of the acceptable values corresponds with a mail exchange record, which is "MX". The list of all accepted values for the type of DNS Record and their description can be found [here](https://en.wikipedia.org/wiki/List_of_DNS_record_types).   
```powershell
PS C:\users\Oracle9\desktop> Get-DnsServerResourceRecord -ZoneName 'UnderTheWire
.tech' -RRType Mx                                                               
                                                                                
HostName                  RecordType Type       Timestamp            TimeToLive 
--------                  ---------- ----       ---------            ---------- 
utw_exch                  MX         15         0                    01:00:00   
                                                                                
                                                                                
PS C:\users\Oracle9\desktop> ls                                                 
                                                                                
                                                                                
    Directory: C:\users\Oracle9\desktop                                         
                                                                                
                                                                                
Mode                LastWriteTime         Length Name                           
----                -------------         ------ ----                           
-a----        8/30/2018  10:51 AM              0 9229

PS C:\users\Oracle9\desktop> $($(Get-DnsServerResourceRecord -ZoneName underthew
ire.tech -RRType Mx).HostName + $(ls).name)                                     
utw_exch9229                                                                                                                                                        
```
<strong>Password:</strong> <code>utw_exch9229</code>
