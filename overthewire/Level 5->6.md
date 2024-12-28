## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

## Approach
We use the <code>find</code> command again. Applying the following filters, given the prompt:
- human-readable: <code>-readable</code>
- 1033 bytes in size: <code>-size 1033c</code>
- not executable: <code>-not -executable</code>

## Solution
```zsh
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ find . -readable -size 1033c -not -executable
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
<strong>Password:</strong> <code>HWasnPhtq9AVKe0dmk45nxy20cvUa6EG</code>
