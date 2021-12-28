[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 5

password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh
solution: DXjZPULLxYr17uwoI01bNLQbtFemEgo7 

## Level Goal  

The password for the next level is stored in a file somewhere under the inhere
directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable

### Commands you may need to solve this level
ls, cd, cat, file, du, find

## Solution
`find . -size 1033c ! -executable`  
