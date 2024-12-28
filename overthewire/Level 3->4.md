## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

## Approach
Use either of the commands: <code>ls -a</code> and <code>ls -la</code> to list <strong>all</strong> files and directories, <em>including <strong>hidden</strong> ones.</em>

## Solution
```zsh
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit4 bandit3   33 Sep 19 07:08 ...Hiding-From-You
```
Alternatively
```zsh
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
```
We learn that the name of the hidden file is <code>...Hiding-From-You</code>. Accessing it, we get the password:
```zsh
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
<strong>Password:</strong> <code>2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ</code>
