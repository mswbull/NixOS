### Flatpak

./flatpak.sh

flatpak install flathub org.mozilla.firefox  
flatpak install flathub org.libreoffice.LibreOffice  
flatpak install flathub md.obsidian.Obsidian  
flatpak install flathub org.gimp.GIMP  
flatpak install flathub org.kde.krita  
flatpak install flathub org.audacityteam.Audacity  
flatpak install flathub org.videolan.VLC  
flatpak install flathub fr.handbrake.ghb  
flatpak install flathub com.obsproject.Studio  
flatpak install flathub com.getpostman.Postman  
flatpak install flathub com.usebottles.bottles  
flatpak install flathub com.github.IsmaelMartinez.teams_for_linux 
flatpak install flathub com.heroicgameslauncher.hgl  
flatpak install flathub com.github.tchx84.Flatseal

---

### NixOS Services

services.fprintd.enable = true;

services.flatpak.enable = true;
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

virtualisation.docker.enable = true;

virtualisation.libvirtd.enable = true;
programs.virt-manager.enable = true;

services.onedrive.enable = true;
onedrive
systemctl --user enable onedrive@onedrive.service
systemctl --user start onedrive@onedrive.service
systemctl --user status onedrive@onedrive.service
journalctl --user -t onedrive | less

---

### NixOS Packages

neofetch  
wget  
git  
google-chrome  
vscode  
ollama  
bitwarden  
godot_4  
steam  

---

### Fonts

fonts.packages = with pkgs; [
  corefonts  
  vistafonts  
  noto-fonts  
  noto-fonts-cjk  
  noto-fonts-emoji  
  liberation_ttf  
  fira-code  
  fira-code-symbols  
  mplus-outline-fonts.githubRelease  
  dina-font  
  proggyfonts  
];

fonts.fontDir.enable = true;

ln -s /run/current-system/sw/share/X11/fonts ~/.local/share/fonts
flatpak --user override --filesystem=$HOME/.local/share/fonts
flatpak --user override --filesystem=$HOME/.icons

---

### Garbage Collection

./update.sh

sudo nix-collect-garbage --delete-older-than 30d  
sudo nixos-rebuild boot --upgrade  
flatpak update -y