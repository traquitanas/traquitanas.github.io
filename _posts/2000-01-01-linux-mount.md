---
title: "Mount"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package, gspread]

#layout: post
#subtitle: Exercícios e Referências
#thumbnail-img: /assets/img/posts/gspread_icon.png
#share-img: /assets/img/posts/gspread_big.png
#cover-img: /assets/img/posts/gspread_big.png
#gh-repo: michelmetran/package_gspread
#gh-badge: [follow, star, watch, fork]
#comments: true
#language: pt-br

---

<br>

## Meus HDs

**HD1**: /dev/sda - 500GB, SSD

- dev/sda1: efi
- dev/sda2: 200GB - SO
- dev/sda3: resto GB - VMs
**HD1**: /dev/sdb - 750GB, SATA
- dev/sdb1: 300GB - Arquivos
- dev/sdb2: resto GB - Geodata

<br>

## Montar Partições

Fui seguindo esse tutorial bastante completo e entendi muita coisa do Fstab: [How to Write an fstab File on Linux](https://www.howtogeek.com/444814/how-to-write-an-fstab-file-on-linux/). Abaixo seguem alguns dos comandos. Tantos outros estão somente no link.

https://wiki.archlinux.org/index.php/NTFS-3G



Conferir espaço em Partições

```bash
df -h
```

Descobrir os códigos UUID das partições

```bash
sudo blkid
```

Cria as partições

```bash
sudo mkdir /media/$USER/Arquivos
sudo mkdir /media/$USER/Geodata
sudo mkdir /media/$USER/VMs
```

Monta a partição

```bash
sudo mount /dev/sdb1 /media/$USER/Arquivos
sudo mount /dev/sdb2 /media/$USER/Geodata
sudo mount /dev/sda3 /media/$USER/VMs
```



Adicionar partições no fstab

```bash
sudo gedit /etc/fstab
```

```bash
# Outras partições do SSD
UUID=e9d6a225-c3f2-4c85-b6a4-e81581bf0a6a	/media/michel/SSD	ext4	rw,auto,user,sync,exec	1	2
UUID=985b0aff-9fef-4df1-b6fa-dd6e1a07843a	/media/michel/VMs	ext4	rw,auto,user,sync,exec	1	2

# Outras partições do HD de 750 do Caddy (rw,auto,user,uid=1000)
#UUID=488A2E2F2C011AEC	/media/michel/Arquivos	ntfs	rw,auto,user,async	1	2
#UUID=000866C43F87D142	/media/michel/Geodata	ntfs	rw,auto,user,async	1	2
UUID=488A2E2F2C011AEC	/media/michel/Arquivos	ntfs-3g	auto,user,exec,uid=1000,gid=1000	1	2
UUID=000866C43F87D142	/media/michel/Geodata	ntfs-3g	auto,user,exec,uid=1000,gid=1000	1	2
```



Ler um arquivo

```bash
cat /etc/fstab
```



Desmonta a partição

```bash
sudo umount /dev/sda1
sudo umount /dev/sdb1
sudo umount /dev/sdb2
```



Dá permissões

```bash
sudo chown [user]:[group] /media/VMs
sudo chown -R michel:michel /media/michel/VMs
sudo chown -R michel:michel /media/michel/Arquivos
sudo chown -R michel:michel /media/michel/Geodata
```



Se quiser tirar os icons de volumes montados do dock

```bash
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
```

<br>

### NTFS Read Only

[StackOVerflow: Why does my NTFS partition mount as read only?](https://askubuntu.com/questions/70281/why-does-my-ntfs-partition-mount-as-read-only)

```bash
sudo apt-get remove ntfsprogs
sudo apt-get install ntfs-3g
```

<br>

### SWAP

```bash
# ddd
sudo swapon -s

# Desabilitando
sudo swapoff -a
```





- https://linuxhint.com/change_swap_size_ubuntu/
- https://www.cloudbooklet.com/how-to-add-swap-space-in-ubuntu-20-04-google-cloud/

