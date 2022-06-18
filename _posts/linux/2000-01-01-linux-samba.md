---
title: "Samba"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package, pandas]

#layout: post
#subtitle: Exercícios e Referências
#thumbnail-img: /assets/img/posts/pandas_icon.png
#share-img: /assets/img/posts/pandas_big.png
#cover-img: /assets/img/posts/pandas_big.png
#gh-repo: michelmetran/package_pandas
#gh-badge: [follow, star, watch, fork]
#comments: true
#language: pt-br
---



Para acessar os arquivos do Windows, bastar usar o Nautilus (equivalente do Windows Explorer) e digitar “smb://asus-i7”. 

```bash
sudo vim /etc/samba/smb.conf
sudo service smbd restart
sudo service nmbd restart
smbclient //192.168.1.104/Michel -U michel -W workgroup
smbclient //asus-i5/home -U michel -W workgroup
sudo smbpasswd -a michel
mkdir /home/michel/Documents/Samba
```

<br>

## Samba

### Ubuntu com Windows

```bash
sudo apt-get update
sudo apt-get install samba
```

```bash
sudo service smbd start
sudo service smbd stop
sudo service smbd restart
```

```bash
sudo smbpasswd -a michel
```



#### Windows com Ubuntu

```
smb://asus-i5/Arquivos/
```





```
sudo gedit /etc/hosts
```





https://askubuntu.com/questions/923306/connecting-to-a-windows-network-with-ubuntu-16-04-lts
