### Links

https://thegrayarea.tech/why-do-people-love-nixos-so-much-a60c363b2b94

https://codemonkeymike.medium.com/getting-started-with-nixos-75985388a15c

https://search.nixos.org/packages

https://flatpak.org/setup/NixOS

---

### Commands

/etc/nixos/configuration.nix
*Define new system configuration

nixos-rebuild switch
*Switch to the configuration defined configuration.nix

sudo nixos-rebuild boot --upgrade
*Upgrade system

nixos-rebuild switch --rollback
*switch to previous configuration

sudo nix-collect-garbage -d
*Retain the current configuration, delete all old ones

sudo nix-collect-garbage -- delete-older-than 30d
*Retain the current configuration, delete older than 30 days

flatpak update -y\
*Update flatpak applications