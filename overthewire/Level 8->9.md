## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Approach
Use <code>uniq -u</code> to find the unique line of text (only occurs once).

## Solution
```zsh
bandit8@bandit:~$ cat data.txt | sort | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
<strong>Password:</strong> <code>4CKMh1JI91bUIZZPXDqGanal4xvAg0JM</code>
