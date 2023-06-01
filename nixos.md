[[LINUX]]

# nixos  

## installation  

## home-manager  
```
nix-channel --add https://github.com/nix-community/home-manager/archive/release-22.11.tar.gz home-manager
nix-channel --update

nix-shell '<home-manager>' -A install
```

## maintenance 
### update system
```
nix-channel --update                 # needed for home-manager
sudo nix-channel --update            

sudo nixos-rebuild switch --upgrade
home-manager switch
```
### optimize system  
```
nix-collect-garbage
sudo nix-collect-garbage      # sometimes useful to run with sudo

nix-store --optimize
```
### repair system  

## flakes  
A [Guide](https://thiscute.world/en/posts/nixos-and-flake-basics/#advantages-of-nix) for Beginners.  
NixOS Setup Guide - Configuration / Home-Manager / [Flakes](https://www.youtube.com/watch?v=AGVXJ-TIv3Y)  


## config  
example configuration of:
- [nixos](configuration-nix.md)
- [home-manager](home-nix.md)


