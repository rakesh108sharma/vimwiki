[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 10

password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
solution: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR 

## Level Goal  

The password for the next level is stored in the file data.txt, which contains
base64 encoded data

### Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Helpful Reading Material
Base64 on [Wikipedia](https://en.wikipedia.org/wiki/Base64)

## Solution
`cat data.txt | base64 -d`  

