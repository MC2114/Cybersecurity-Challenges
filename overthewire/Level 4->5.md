## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## Approach
We know that the file we are looking for is the only <strong>human-readable</strong> one in the directory. Therefore, we would list all of the file types in the <code>inhere</code> directory and check the file that fits. 

## Solution
The <code>file ./</code> command show the file type for any given files.
By looping through all of the files in the directory, we learn that <code>file07</code> is the only one with <code>ASCII</code> text, which is human-readable.
```zsh
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
bandit4@bandit:~/inhere$ for f in $(ls); do file ./$f; done
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
```
Alternatively, we can deduce from the prompt that the file would most commonly be in <code>ASCII</code> text. 
Usine the <code>find</code> command:
```zsh
bandit4@bandit:~/inhere$ find -type f ! -executable -exec file {} + | grep ASCII./-file07: ASCII text
file07: ASCII text
```
We learn that the password is in <code>file07</code>. Accessing it, we get the password:
```zsh
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
<strong>Password:</strong> <code>4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw</code>
