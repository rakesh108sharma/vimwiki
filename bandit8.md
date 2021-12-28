[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 8

password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
solution: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR 

## Level Goal  

The password for the next level is stored in the file data.txt and is the only
line of text that occurs only once

### Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Helpful Reading Material
Piping and [Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)

## solution
`sort data-txt | uniq -u`
