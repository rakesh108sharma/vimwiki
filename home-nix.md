[[LINUX]]

# home.nix  -  config file of home-manager  

{ config, pkgs, ... }:

{
  # Home Manager needs a bit of information about you and the
  # paths it should manage.
  home.username = "nixer";
  home.homeDirectory = "/home/nixer";

  # This value determines the Home Manager release that your
  # configuration is compatible with. This helps avoid breakage
  # when a new Home Manager release introduces backwards
  # incompatible changes.
  #
  # You can update Home Manager without changing this value. See
  # the Home Manager release notes for a list of state version
  # changes in each release.
  home.stateVersion = "22.11";

  # Let Home Manager install and manage itself.
  programs.home-manager.enable = true;

  programs = {
    htop.enable = true;
    git.enable = true;
    firefox.enable = true;
    chromium.enable = true;
    lf = {
      enable = true;
      keybindings = {
      	"."  = "set hidden!";
      };	
    };
    helix = {
      enable = true;
      settings = {
      	theme = "nord";
      	editor = {
      	  line-number = "relative";
      	  cursor-shape = {
      	  	insert = "bar";
      	  	normal = "block";
      	  	select = "underline";
      	  };
      	  file-picker.hidden = true;	
      	};
      	keys.normal = {
      	  esc = [ "collapse_selection" "keep_primary_selection" ];
      	  space.q = ":q";
      	  space.Q = ":q!";
      	  space.W = ":wq";  	
      	};
      };	
    };
  };
  
  home.packages = with pkgs; [
    most bat exa fd ripgrep ncdu duf  
    fff fzf
    mpv ffmpeg_5-full
    keepassx
    brave librewolf lynx
    transmission
  ];

  home.file = {
#    ".config/helix/config.toml".text = ''
#      theme = "nord"
#    '';
  };
  imports = [ ./versuch.nix ];
}

