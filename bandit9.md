[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 9

password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
solution: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk 

## Level Goal  

The password for the next level is stored in the file data.txt in one of the few
human-readable strings, preceded by several ‘=’ characters.

### Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Solution
`strings data.txt | grep '=='`  

