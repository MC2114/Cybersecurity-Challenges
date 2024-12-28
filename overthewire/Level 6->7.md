## Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

## Approach
For this level, the password is not in a given directory (like <code>inhere</code> in previous levels) but rather <strong>somewhere</strong> on the server. Therefore, we use <code>find /</code>

We use the <code>find</code> command again. Applying the following filters, given the prompt:
- owned by user bandit7: <code>-user bandit7</code>
- owned by group bandit6: <code>-group bandit6</code>
- 33 bytes in size: <code>-size 33c</code>

To minimize output to the terminal, we want to add <code>2>/dev/null</code> to redirect all errors to <code>/dev/null</code>

## Solution
```zsh
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
<strong>Password:</strong> <code>morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj</code>
