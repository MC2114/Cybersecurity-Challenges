## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory

## Approach
Wrap the file name in <code>" "</code> or use <code>\ </code> syntax per space between file name characters.

## Solution
```zsh
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
Alternatively
```zsh
bandit2@bandit:~$ cat spaces\ in\ this\ filename
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
<strong>Password:</strong> <code>MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx</code>
