## Level Goal
The password for Century8 is in a readme file somewhere within the contacts, desktop, documents, downloads, favorites, music, or videos folder in the user’s profile.

## Solution
- Since we do not know the exact location of the readme file =, we can use <code>Get-ChildItem -Recurse</code> or <code>ls -R</code> to search through all the files and folders.
- We know that the file is called <code>readme</code>, therefore we can use the syntax -like "*readme*"
- Use <code>Get-Content</code> or <code>gc</code> to access the content of the file.
```powershell
PS C:\users\century7\Downloads> gc $(ls -R | ? {$_.name -like "*readme*"}).fullname    
7points                        
```
<strong>Password:</strong> <code>7points</code>
