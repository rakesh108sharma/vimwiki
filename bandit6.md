[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 6

password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7
solution: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs 

## Level Goal  

The password for the next level is stored somewhere on the server and has all of
the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

### Commands you may need to solve this level
ls, cd, cat, file, du, find, grep

## Solution
`find . -user bandit7 -group bandit6 -size 33c`
