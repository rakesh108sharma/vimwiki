[[LINUX]]
# git

### simple steps to start a new project
```
git init
git add .
git commit -m "MESSAGE"
git push
```
### local repo -> remote repo
- create empty repo on gitlab
- create new token
- `git push --set-upstream https://github.com/USERNAME/REPONAME.git master`


### manage dotfiles with a bare git repository

1. create a bare repository  
`git init --bare $HOME/.dotfiles`
2. add an alias for git in .bashrc AND run the command  
`echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc`  
3. make sure "unwanted" files are not being tracked  
`config config --local status.showUntrackedFiles no`


now do the usual "git stuff":  
add $$ commit $$ push a file  

```
config add .bashrc
config commit -m "added bashrc"
config push  
```  

(push wird nicht wirklich benötigt?!)    
`config status`  


fuktionierte erst hiernach:    

```
config remote add origin .versuch/      
config push --set-upstream origin master  
```
---- 

### rollback  - Dinge ungeschehen machen
git reset | restore | revert

1. working directory has been changed BUT nothing has been commited yet:  
  `git reset`

2. you want to restore a file from a specific commit:  
`git restore --source HEAD~2 <FILENAME>`  
  (HEAD~2 ==> second last commit)  
  (you can chack the commits with: git log)  

3. you want to completely revert to a previous commit:  
  (all inbetween steps will be lost)  
`git revert HEAD~4`  
