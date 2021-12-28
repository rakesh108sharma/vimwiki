
[Bandit](Bandit.md)     [[HACKING]]     [[LINUX]]

# Bandit - level 24

password: UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
solution: uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG 

## Level Goal  

A daemon is listening on port 30002 and will give you the password for bandit25
if given the password for bandit24 and a secret numeric 4-digit pincode. There
is no way to retrieve the pincode except by going through all of the 10000
combinations, called brute-forcing.

## Solution

1. We can connect on port 30002 in a same way as we have done in level 20. We
   also have to pass password for current level and the 4 digit pin.The command
   is:
   `nc localhost 30002  UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ ****`
2. first we write a script **bruteforce.sh** which will create all possible combinations and write
   those in a text file:
   ```
   #!/bin/bash
   for i in {0000..9999}
   do 
    echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i"
   done
   ```
1. `./bruteforce.sh > combinations.txt`
2. `nc localhost 30002 < combinations.txt`




