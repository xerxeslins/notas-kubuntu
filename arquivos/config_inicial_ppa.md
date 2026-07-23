## Atualização base
```bash
sudo apt update && sudo apt full-upgrade -y

```

## Utilitários de descompactação

```bash
sudo apt install -y p7zip-full lzma lzop unrar rar zip unzip

```

## Codecs multimídia restritos

```bash
sudo apt install -y kubuntu-restricted-extras libavcodec-extra

```

## Fontes da Microsoft (Core Fonts)

Aceite automático do EULA:

```bash
echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections
sudo apt install -y ttf-mscorefonts-installer
fc-cache -f -v

```

## Flatpak e integração com KDE Discover

```bash
sudo apt install -y flatpak plasma-discover-backend-flatpak
flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

```

## Steam (suporte i386)

```bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install -y steam-installer

```

## Firewall e Backup (UFW e Timeshift)

```bash
sudo apt install -y ufw timeshift
sudo ufw enable

```

## zRAM (Swap compactada na memória)

```bash
sudo apt install -y zram-config
sudo systemctl start zram-config

```

Verificação:

```bash
zramctl
swapon --show

```

## PPA Kubuntu Backports

```bash
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt update && sudo apt full-upgrade -y
sudo reboot

```
