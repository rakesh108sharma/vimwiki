
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 26

password: 5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z 
solution: 3ba3118a22e93127a4ed485be72ef5ea 

## Level Goal  

Good job getting a shell! Now hurry and grab the password for bandit27!

### Commands you may need to solve this level
ls

## Solution
Same problem we had on level 25 when trying to ssh into level 26.
bandit27 has no login shell, instead the **more** pager prints out a text. Once
printed the more command ends and the connection is closed.
1. first we have to force the more command in not being able to print the whole
   message at once:
   resize the window! make it really small!
2. within the **more** command pressing **v** will execute the editor with the
   active text file. (editor is vi).
3. in **vi** we first set the **shell** variable and then call the shell:
   `:set shell=/bin/bash`
   `:shell`
4. we are now in bandit27#s shell  
   running the present script:
   `./bandit27-do cat /etc/bandit_pass/bandit27`
   


