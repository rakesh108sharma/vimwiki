[[LINUX]]

# configuration.nix  -  config file of nixos  

# Edit this configuration file to define what should be installed on
# your system.  Help is available in the configuration.nix(5) man page
# and in the NixOS manual (accessible by running ‘nixos-help’).

{ config, pkgs, ... }:

{
  imports =
    [ # Include the results of the hardware scan.
      ./hardware-configuration.nix
    ];

  nix.settings.experimental-features = [ "nix-command" "flakes" ];

  # Bootloader.
  boot.loader.grub.enable = true;
  boot.loader.grub.device = "/dev/sda";
  boot.loader.grub.useOSProber = true;



#####   N E T W O R K I N G   	#####
  networking = {
    hostName = "nixos"; # Define your hostname.
    # networking.wireless.enable = true;  # Enables wireless support via wpa_supplicant.

    # Configure network proxy if necessary
    # networking.proxy.default = "http://user:password@proxy:port/";
    # networking.proxy.noProxy = "127.0.0.1,localhost,internal.domain";

    # Enable networking
    networkmanager.enable = true;
    dhcpcd.enable = false;
  
    interfaces.enp3s0.ipv4.addresses = [ {
      address = "192.168.1.12";
      prefixLength = 24;
    } ];
    defaultGateway = "192.168.1.1";
    nameservers = [ "1.1.1.1" ];
    enableIPv6 = false;
    #firewall = {
    #	enable = true;
    #	allowedTCPPorts = [ 6881 ];
    #	allowedUDPPorts = [ 6882 ];
    #};
  };

#####   S Y S T E M   #####
  # Set your time zone.
  time.timeZone = "Europe/Brussels";

  # Select internationalisation properties.
  i18n.defaultLocale = "en_US.UTF-8";

#####   S E R V I C E S   #####
  services = {
  	xserver = {
  	  # Enable the X11 windowing system.
      enable = true;
      # Configure keymap in X11
      layout = "de";
      xkbVariant = "";

      # Enable the XFCE Desktop Environment.
      displayManager = {
        lightdm.enable = true;
        autoLogin.enable = true;
        autoLogin.user = "nixer";
      };
      #  services.xserver.desktopManager.xfce.enable = true;
      #  available: xfce plasma5 pantheon mate lxqt gnome cinnamon 
      #  windowManager: twm tinywm smallwm ratpoison leftwm berry 
      #  dwm cwm bspwm
      #  i3 awesome herbstluftwm qtile xmonad 
      #  openbox fluxbox 
      #  lisp: sawfish spectrwm stumpwm
      desktopManager.plasma5.enable = true;   
  	};

  	# Enable the OpenSSH daemon.
  	openssh.enable = true;
        fstrim.enable = true;
  };


  # Configure console keymap
  console.keyMap = "de";

  # Enable CUPS to print documents.
#  services.printing.enable = true;

  # Enable sound with pipewire.
  sound.enable = true;
  hardware.pulseaudio.enable = false;
  security.rtkit.enable = true;
  services.pipewire = {
    enable = true;
    alsa.enable = true;
    alsa.support32Bit = true;
    pulse.enable = true;
    # If you want to use JACK applications, uncomment this
    #jack.enable = true;

    # use the example session manager (no others are packaged yet so this is enabled by default,
    # no need to redefine it in your config for now)
    #media-session.enable = true;
  };

  # Enable touchpad support (enabled default in most desktopManager).
  # services.xserver.libinput.enable = true;

  # Define a user account. Don't forget to set a password with ‘passwd’.
  users.users.nixer = {
    isNormalUser = true;
    description = "nixer";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
    #  thunderbird
    ];
  };

  # Allow unfree packages
  nixpkgs.config.allowUnfree = true;


#####   E N V I R O N M E N T   #####
  # List packages installed in system profile. To search, run:
  # $ nix search wget
  environment.systemPackages = with pkgs; [
  #  vim # Do not forget to add an editor to edit configuration.nix! The Nano editor is also installed by default.
  #  wget
  #xfce.thunar-volman
  #volumeicon
  micro
  ];          # END system packages

  programs = {
    bash.enableCompletion = true;
    nano.nanorc = {
      set autoindent
      set tabsize 2

      bind ^S savefile main
      bind ^Q exit main
    };
  };          # END programs

  environment.localBinInPath = true;

  environment.variables = {
  	EDITOR = "micro";
  	PAGER = "most";
  	MANPAGER = "most";
  };          # END variables

  environment.shellAliases = {
    ls = "exa -s type";
    la = "exa -a -s type";
    ll = "exa -l -s type --git --icons";
    e = "micro";
    E = "sudo micro";
    ee = "hx";
    EE = "sudo hx";
    ff = "lf";	
    
    duu = "ncdu -e";
    duf = "duf -only local";
    cat = "bat";
    yyh = "home-manager edit";
    yyn = "nixos-rebuild edit";
    yyhh = "home-manager switch";
    yynn = "sudo nixos-rebuild switch";
    yyu = "apply-update.sh";
    yyc = "apply-optimize.sh";
  };          # END aliases


  
# Some programs need SUID wrappers, can be configured further or are
  # started in user sessions.
  # programs.mtr.enable = true;
  # programs.gnupg.agent = {
  #   enable = true;
  #   enableSSHSupport = true;
  # };


  # This value determines the NixOS release from which the default
  # settings for stateful data, like file locations and database versions
  # on your system were taken. It‘s perfectly fine and recommended to leave
  # this value at the release version of the first install of this system.
  # Before changing this value read the documentation for this option
  # (e.g. man configuration.nix or on https://nixos.org/nixos/options.html).
  system.stateVersion = "22.11"; # Did you read the comment?
}

