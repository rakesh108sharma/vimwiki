[[LINUX]]
# container

## Probleme bei templates

Probleme by Templates scheint mit 'postfix' service zusammenzuhängen.

Eine mögliche Lösung:       
    1. create container with 'unprivileged container' **unselected**     
    2. in the pve-shell:    
        `vzdump [CT id number] --exclude-path /var/spool/postfix/dev/random --exclude-path
        /var/spool/postfix/dev/urandom --storage [STORAGE]`   
    3. delete the CT    
    4. restore the backup with 'unprivileged container' **selected**    

## Alpine Linux
Alpine eignet sich besonders als CT.   
benötigt nur ~50MB   

### minimum setup
`apk add nano sshd`   

>nano /etc/ssh/sshd_config    
     PermitRootLogin yes    

`rc-update add sshd`   
`rc-service sshd start`     

>
`nano ~/.nanorc`    
include /usr/share/nano/*   
set smooth   
set autoindent    
set morespace     
set tabsize 4    
set tabstospaces    
set nowrap    
set constantshow #display cursor position    
set suspend #allow nano to be suspended    
set nohelp    
>
bind ^F whereis main    
bind ^N findnext main    
bind ^P findprevious main    
bind ^Space mark main    
bind ^U undo main    
bind ^R replace main     
bind ^R regexp search    
bind ^I insert main    
bind ^I flipexecute insert    
>
bind ^Q exit main    
bind ^S savefile main    

----

>`nano ~/.profile`    
export MANPAGER=less    
export PAGER=less    
export EDITOR=nano    
export HISTSIZE=1000    
export HISTFILESIZE=1000    
export CDPATH='~'    
>  
alias ls='ls --color=auto'   
alias ll='ls -lh'    
alias la='ls -a'    
alias ..='cd ..'    
alias ...='cd ../..'    
alias ....='cd ../../..'    
alias ~='cd $HOME'    
alias c='clear'    
alias _='sudo'    
>
alias v='vim'    
alias grep='grep --color'    
alias du='du -ach | sort -hr | most'    
alias df='df -h | grep /dev/sd | sort -k 1'    

 
