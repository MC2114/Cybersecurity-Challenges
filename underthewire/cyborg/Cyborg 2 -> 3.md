## Level Goal
The password for cyborg3 is the host A record IP address for CYBORG718W100N PLUS the name of the file on the desktop.

## Solution
Use <code>Resolve-DnsName</code> cmdlet to find the IP address of the user CYBORG718W100N.
```powershell
PS C:\users\cyborg2\desktop> $($(Resolve-DnsName CYBORG718W100N).IPAddress + $(ls).name
)
172.31.45.167_ipv4
```
<strong>Password:</strong> <code>172.31.45.167_ipv4</code>
