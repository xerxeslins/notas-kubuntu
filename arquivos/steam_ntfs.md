## Configurar Steam Nativa (DEB) em Partição NTFS (Kubuntu)

### 1. Identificar UUID da partição
```bash
lsblk -f

```

Anote o `UUID` da partição NTFS. (Assume-se UID/GID `1000`, verifique com `id -u`). 

### 2. Ponto de montagem e FSTAB

Crie o diretório e insira a regra de montagem automática, exemplo com UUID = `0C73521E255F5FF5`:

```bash
sudo mkdir -p /mnt/meusjogos

sudo bash -c 'cat >> /etc/fstab << "EOF"
UUID=0C73521E255F5FF5  /mnt/meusjogos  ntfs-3g  defaults,uid=1000,gid=1000,umask=000,exec  0  0
EOF'

sudo mount -a

```

### 3. Link Simbólico (Proton Compatdata)

O Proton exige sistema de arquivos nativo para os arquivos de compatibilidade. Crie as pastas e o atalho apontando para o seu diretório pessoal:

```bash
mkdir -p /mnt/meusjogos/SteamLibrary/steamapps
mkdir -p ~/.local/share/Steam/steamapps/compatdata_ntfs

ln -s ~/.local/share/Steam/steamapps/compatdata_ntfs /mnt/meusjogos/SteamLibrary/steamapps/compatdata

```

### 4. Adicionar na Steam

1. Abra a Steam.
2. Acesse **Configurações** > **Armazenamento**.
3. Clique em **(+)** para adicionar unidade local.
4. Selecione o caminho `/mnt/meusjogos/SteamLibrary`.

```
