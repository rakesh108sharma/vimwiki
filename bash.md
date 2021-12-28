[[LINUX]]
# bash 

## super useful bash "extensions"/prg
    - exa               (# ls)
    - bat               (# cat)
    - ripgrep           (# grep)
    - hstr              (# history)
    - fd, fselect       (# find)
    - starship          (# prompt)
    - fzf, fzy          (fuzzy finder helper programs)
    - mdcat             (cat for markdown)

## links
[cheatsheet](https://devhints.io/bash)  
[40 Simple Yet Effective Linux Shell Script Examples](https://www.ubuntupit.com/simple-yet-effective-linux-shell-script-examples/)  
[bash hackers wiki](https://wiki.bash-hackers.org/)  
[bash guide](https://guide.bash.academy/)  
[pure Bash Bible](https://github.com/dylanaraps/pure-bash-bible)
[bash shell-scripting libraries](https://dberkholz.com/2011/04/07/bash-shell-scripting-libraries/)

## color/escape codes

| color   | fg | bg |
|---------|----|----|
| black   | 30 | 40 |
| red     | 31 | 41 |
| green   | 32 | 42 |
| yellow  | 33 | 43 |
| blue    | 34 | 44 |
| magenta | 35 | 45 |
| cyan    | 36 | 46 |
| white   | 37 | 47 |

| style         | value |
|---------------|-------|
| no style      | 0     |
| bold          | 1     |
| low intensity | 2     |
| underline     | 4     |
| blinking      | 5     |
| reverse       | 7     |
| invisible     | 8     |

```bash
echo -e "SOME REXT AND CODES

\033[0m          reset
\033[5m          flashing
\033[5;34;43m    flashing blue on red
```


## dotfiles
### .bashrc
[.bashrc](vfile:/home/maya/.bashrc)

```
# .bashrc

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

[ -f "$HOME"/.bash_colors ] && . "$HOME"/.bash_colors
[ -f "$HOME"/.bash_exports ] && . "$HOME"/.bash_exports

export PATH=$HOME/bin:$PATH
export MANPAGER=most
export PAGER=most
export EDITOR=nano
export BROWSER=chromium
export HISTSIZE=1000
export HISTFILESIZE=1000
export SHELL=/bin/bash
export CDPATH='~'

#PS1='[\u@\h \W]\$ '
PS1="\n${cyan}\h: ${reset_color} ${yellow}\w\n${reset_color}-> "

shopt -s cdspell

#####   A L I A S   #####
# system
alias zzz='sudo /usr/bin/zzz'
#alias qqq='sudo poweroff'
alias fw='sudo iptables -nvL'
alias fw_watch='watch -n 5 sudo iptables -nvL'
alias ee='sudo nano $(find /etc/ -type f |fzy -l 15)'
alias eee='clear && cd /etc && ls'
alias sss='clear && cd /var/service/ && ls && sudo sv s /var/service/*'
alias vsv='sudo vsv'

# terminal
alias ls='ls --color=auto'
alias ll='ls -lh'
alias la='ls -a'
alias l='exa -l'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias ~='cd ~'
alias c='clear'
alias _='sudo'

# packet manager
alias yyu='echo -e "sudo xbps-install -Su\n" && sudo xbps-install -Su'
alias yyx='sudo xbps-install -uy xbps'
#yys = function for searching packages
#yyss = function fuzzy search for a package 
alias yyr='echo -e "sudo xbps-remove\n" && sudo xbps-remove'
#yyrr = function fuzzy search AND remove
alias yyl='echo -e "sudo xbps-query -l | most\n" && sudo xbps-query -l | most'
alias yyi='echo -e "sudo xbps-install\n" && sudo xbps-install'
#yyii = function fuzzy search AND install
alias yyc='echo -e "sudo xbps-remove -o\n" && sudo xbps-remove -o'
alias yycc='echo -e "sudo xbps-remove -O\n" && sudo xbps-remove -O'

# other
alias cat='bat --pager less'
alias e='nano $(find $HOME | fzy -l 15)'
alias vv='vim $(find $HOME | fzy -l 15)'
alias v='vim'
alias gg='glances'
alias grep='grep --color'
alias qmv='qmv -e vim'
alias qcp='qcp -e vim'
alias du='du -ach | sort -hr | most'
alias df='df -h | grep /dev/sd | sort -k 1'
alias mplayer='mplayer -af volnorm'
alias wetter='curl -4 http://wttr.in/Eupen'
alias yv='youtube-viewer --resolution=720p -C'
alias n='dnote'
alias f='sudo fd'
alias wiki-='taizen --lang=en'
alias wiki-de='taizen --lang=de'
alias wiki-es='taizen --lang=es'
alias wiki-fr='taizen --lang=fr'
alias wiki-la='taizen --lang=la'
#####   END ALIAS   #####


#####   F U N C T I O N S   #####
[ -f "$HOME"/.bash_functions ] && . "$HOME"/.bash_functions

uu() { udevil umount /dev/sd"$1" ; }     # unmount usb devices

myip ()
{
    echo
    #value=$(curl -s checkip.dyndns.org | grep -Eo '[0-9\.]+')
    value=$(curl -s http://ipecho.net/plain)
    echo -e "${echo_bold_green} $value ${echo_normal}"
    echo
}

yys ()
{
echo -e "LOCAL\tsudo xbps-query -s\n" && sudo xbps-query -s "$1"
echo
echo -e "REPO\tsudo xbps-query -Rs\n" && sudo xbps-query -Rs "$1"
}

yyii ()
{
sudo xbps-install "$(xbps-query -Rs '' | fzy -l 25 | awk '{ print $2}')"
}

yyrr ()
{
sudo xbps-remove "$(xbps-query -s '' | fzy -l 15 | awk '{ print $2}')"
}

kernel ()
{
    clear
    uname -a
    echo
    ls /boot/v*
    echo
    vkpurge list
}


down4me () { curl -s "http://www.downforeveryoneorjustme.com/$1" | sed '/just you/!d;s/<[^>]*>//g' ; }
mkcd () {  mkdir -p -- "$*"; cd -- "$*" ; }
copy () { scp $@ void@192.168.1.12: ; }



#####   END FUNCTIONS   #####

############################################################

### make LESS colourful
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;33m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;42;30m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;36m'


### HSTR configuration - add this to ~/.bashrc
alias hh=hstr                    # hh to be alias for hstr
export HSTR_CONFIG=hicolor       # get more colors
shopt -s histappend              # append new history items to .bash_history
export HISTCONTROL=ignorespace   # leading space hides commands from history
export HISTFILESIZE=10000        # increase history file size (default is 500)
export HISTSIZE=${HISTFILESIZE}  # increase history size (default is 500)
# ensure synchronization between Bash memory and history file
#export PROMPT_COMMAND="history -a; history -n; ${PROMPT_COMMAND}"
# if this is interactive shell, then bind hstr to Ctrl-r (for Vi mode check doc)
if [[ $- =~ .*i.* ]]; then bind '"\C-r": "\C-a hstr -- \C-j"'; fi
# if this is interactive shell, then bind 'kill last command' to Ctrl-x k
if [[ $- =~ .*i.* ]]; then bind '"\C-xk": "\C-a hstr -k \C-j"'; fi
### END HSTR
#export QT_SCALE_FACTOR=0.9


# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/home/maya/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/home/maya/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/home/maya/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/home/maya/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<

### starship prompt # must be the last entry in bashrc
#alias config='/bin/git --git-dir=/home/maya/.versuch --work-tree=/home/maya'
#eval "$(starship init bash)"
```

###.bashrc notes
export CDPATH='~' will let you cd into your home folders from anywhere in the filesystem

### .bash_profile
[.bash_profile](vfile:/home/maya/.bash_profile)

```
# .bash_profile

# Get the aliases and functions
[ -f $HOME/.bashrc ] && . $HOME/.bashrc

devmon &
```
