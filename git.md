[[LINUX]]
# git

## simple steps to start a new project
```
git init
git add .
git commit -m "MESSAGE"
git push
```
## local repo -> remote repo
- create empty repo on gitlab
- create new token
- `git push --set-upstream https://github.com/USERNAME/REPONAME.git master`


## manage dotfiles with a bare git repository
### setting up / creatin a new repo from scratch
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
config remote add origin <remote-URL>      
config push --set-upstream origin master  
```
---- 

### Install your dotfiles on a new system
1. `echo ".dotfiles" >> .gitignore`
2. `git clone --bare <remote-git-repo-URL> $HOME/.dotfiles`
3. `alias config='/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME'`
4. `config config --local status.showUntrackedFiles no`
5. `config checkout`
   (..might fail if some files already exists
   delete/move the files and repeat checkout)
(add the alias to .bashrc/.zshrc)



## rollback  -- Dinge ungeschehen machen
git reset | restore | revert

1. working directory has been changed BUT nothing has been staged/commited yet:  
  `git restore`

2. files have been staged:
  `git restore --staged`
  
3. you want to restore a file from a specific commit:  
`git restore --source HEAD~2 <FILENAME>`  
  (HEAD~2 ==> second last commit)  
  (you can check the commits with: git log)  

4. you want to completely revert to a previous commit:  
  (all inbetween steps will be lost)  
`git revert HEAD~4`  
