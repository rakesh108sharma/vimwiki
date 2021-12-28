[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 4

password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB 
solution: koReBOKuIDDepwhWk7jZC0RTdopnAYKh 

## Level Goal  

The password for the next level is stored in the only human-readable file in the
inhere directory. Tip: if your terminal is messed up, try the “reset” command.

### Commands you may need to solve this level
ls, cd, cat, file, du, find

## Solution
```
cd inhere
for f in *; do file -- "$f"; done
cat ./-file07
```

