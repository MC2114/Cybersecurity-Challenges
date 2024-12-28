## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Approach
Use <code>base64 -d</code> to decode the file data.txt.
  
## Solution
```zsh
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
<strong>Password:</strong> <code>dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr</code>
