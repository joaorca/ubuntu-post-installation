# Software Updates
sudo apt update && sudo apt upgrade --assume-yes
sudo apt autoremove --assume-yes

# System Tweaks
gsettings set org.gnome.desktop.interface show-battery-percentage true
gsettings set org.gnome.shell.extensions.dash-to-dock click-action minimize
gsettings set org.gnome.nautilus.preferences default-sort-order type

# Softwares
sudo apt install --assume-yes curl neovim git kill
sudo apt install --assume-yes gnome-tweaks
sudo apt install --assume-yes gnome-shell-extension-manager
sudo apt install --assume-yes ubuntu-restricted-extras
sudo apt install --assume-yes unzip p7zip unrar 

# Enable Flatpak Support
sudo apt install --assume-yes flatpak
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
sudo apt install --assume-yes gnome-software-plugin-flatpak

# Flatpak Softwares
flatpak install flathub -y com.discordapp.Discord

# Rust Tools
sudo apt install --assume-yes cargo
cargo install bat exa ytop

# Fish Terminal
sudo apt install --assume-yes fish
sudo usermod -s /usr/bin/fish $(whoami)

chsh -s $(which fish)
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source
fisher install jorgebucaran/fisher
fisher install jhillyerd/plugin-git
fisher install gazorby/fish-exa
fisher install IlanCosman/tide@v5

~/.config/fish/config.fish
command -qv nvim && alias vim nvim
set -gx PATH ~/.cargo/bin $PATH

# VS Code
sudo apt-get install wget gpg && wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && sudo install -D -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/microsoft.gpg && rm -f microsoft.gpg

/etc/apt/sources.list.d/vscode.sources
Types: deb
URIs: https://packages.microsoft.com/repos/code
Suites: stable
Components: main
Architectures: amd64,arm64,armhf
Signed-By: /usr/share/keyrings/microsoft.gpg

sudo apt install apt-transport-https && sudo apt update && sudo apt install code

# 1Password
curl -sS https://downloads.1password.com/linux/keys/1password.asc | sudo gpg --dearmor --output /usr/share/keyrings/1password-archive-keyring.gpg

echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/1password-archive-keyring.gpg] https://downloads.1password.com/linux/debian/amd64 stable main' | sudo tee /etc/apt/sources.list.d/1password.list

sudo mkdir -p /etc/debsig/policies/AC2D62742012EA22/

curl -sS https://downloads.1password.com/linux/debian/debsig/1password.pol | sudo tee /etc/debsig/policies/AC2D62742012EA22/1password.pol

sudo mkdir -p /usr/share/debsig/keyrings/AC2D62742012EA22

curl -sS https://downloads.1password.com/linux/keys/1password.asc | sudo gpg --dearmor --output /usr/share/debsig/keyrings/AC2D62742012EA22/debsig.gpg

sudo apt update && sudo apt install --assume-yes 1password

# Gnome Extensions
https://extensions.gnome.org/extension/1460/vitals/
https://extensions.gnome.org/extension/355/status-area-horizontal-spacing/
https://extensions.gnome.org/extension/3843/just-perfection/
https://extensions.gnome.org/extension/4158/gnome-40-ui-improvements/

# JetBrains ToolBox
sudo ./install-jetbrains.sh 
/opt/jetbrains-toolbox/jetbrains-toolbox
