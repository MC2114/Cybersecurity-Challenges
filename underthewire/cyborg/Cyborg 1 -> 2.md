## Level Goal
The password for cyborg2 is the state that the user Chris Rogers is from as stated within Active Directory.

## Solution
- Use <code>Get-ADUser</code> cmdlet to access the users within the AD.
- Filter the users using <code>-Filter {GivenName -eq 'Chris' -and Surname -eq 'Rogers'}</code>
- Our objective is to find the state in which the user Chris Rogers lives, therefore we add the parameter <code>-Properties State</code>
```powershell
PS C:\users\cyborg1\desktop> $user = Get-ADUser -Filter {GivenName -eq 'Chris' -and Sur
name -eq 'Rogers'} -Properties State
PS C:\users\cyborg1\desktop> $($user).State                                            
kansas  
```
<strong>Password:</strong> <code>kansas</code>
