## Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

## Approach
Use <code>grep "millionth"</code> to get the password next to the word millionth.

## Solution
```zsh
bandit7@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  data.txt  .profile
bandit7@bandit:~$ cat data.txt | grep "millionth"
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
<strong>Password:</strong> <code>dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc</code>
