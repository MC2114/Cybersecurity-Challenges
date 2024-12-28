## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Approach
- Use <code>strings</code> command to output only human-readable strings.
- Use <code>-grep "="</code> command to find the string preceded by several ‘=’ characters.
  
## Solution
```zsh
bandit9@bandit:~$ strings data.txt | grep "="
}========== the
p\l=
;c<Q=.dEXU!
3JprD========== passwordi
qC(=	
~fDV3========== is
7=oc
zP=	
~de=
3k=fQ
~o=0
69}=
%"=Y
=tZ~07
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
N=~[!N
zA=?0j
```
<strong>Password:</strong> <code>FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey</code>
