## Level Goal
The password for groot11 is the one word that makes the two files on the desktop different.

## Solution
We first look at the 2 files present on the desktop: <code>new.txt</code> and <code>old.txt</code>. By the challenge, we can assume that these <code>.txt</code> files are different by 1 word and we need to look for a cmdlet that allows us to compare the 2 files most efficiently. 
```powershell
PS C:\users\Groot10\desktop> ls


    Directory: C:\users\Groot10\desktop


Mode                LastWriteTime         Length Name                          
----                -------------         ------ ----                          
-a----        8/30/2018   5:52 AM          17324 new.txt                       
-a----        8/30/2018   5:52 AM          17313 old.txt
```
By looking through the commands available from the documentations, we find that the <code>Compare-Object</code> cmdlet would be suitable for this task. It requires 2 objects for comparison, the <code>ReferenceObject</code> (indicated by <code><=</code>) and the <code>DifferenceObject</code> (indicated by <code>=></code>). Thus, we will store the 2 text files into 2 variables: <code>new</code> and <code>old</code> to compare.
```powershell
PS C:\users\Groot10\desktop> $old = $(cat old.txt)
PS C:\users\Groot10\desktop> $new = $(cat new.txt)
PS C:\users\Groot10\desktop> Compare-Object -ReferenceObject $old -DifferenceObj
ect $new

InputObject SideIndicator
----------- -------------
taserface   =>           
                     
```
<strong>Password:</strong> <code>taserface</code>
