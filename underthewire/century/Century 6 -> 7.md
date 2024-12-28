## Level Goal
The password for Century7 is the number of folders on the desktop.	

## Solution
The <code>ls -Directory</code> command lists all of the folders on the desktop, and we can use <code>.Count</code> to tally the total number.
```powershell
PS C:\users\century6\desktop> $(ls -Directory).Count
197 
```
<strong>Password:</strong> <code>197</code>
