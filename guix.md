[[LINUX]] [[LISP]]
# guix package manager
## install
```
cd /tmp
wget https://git.savannah.gnu.org/cgit/guix.git/plain/etc/guix-install.sh
chmod +x guix-install.sh
./guix-install.sh
```

say **yes** to *permit downloading pre-build package binaries*
otherwise everything needs to be build from source.

on VOIDLINUX the daemon needs to be started manually:
```
~root/.config/guix/current/bin/guix-daemon \
       --build-users-group=guixbuild
```

Make sure these lines are in your ~/.bash_profile OR ~/.zprofile
```
GUIX_PROFILE="$HOME/.guix-profile"
. "$GUIX_PROFILE/etc/profile"
```

`guix pull`

Important! Adding another GUIX_PROFILE:
```
GUIX_PROFILE="$HOME/.config/guix/current"
. "$GUIX_PROFILE/etc/profile"
```

update (again):
```
guix pull
guix pull --news
guix upgrade
```

- upgrading the guix tool which belongs to root:
`sudo -i guix pull`

## Setting the locale correctly
As we saw while installing the emacs package, guix will repeatedly write out
warnings about setlocale: LC_ALL: cannot change locale. You can fix this issue
by running this command (as sudo!):
```
sudo guix install glibc-locales
sudo vim /root/.profile
```

Now edit the file /root/.profile with your preferred text editor (as sudo) and
add the following line:
`GUIX_LOCPATH=$HOME/.guix-profile/lib/locale`



