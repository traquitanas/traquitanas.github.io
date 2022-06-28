---
title: "Virtual Box: Command Line"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package, pandas]
#layout: post
#title: Jupyter Notebook
#subtitle: Exercícios e Referências
#tags: [python, pycharm, jupyter, package]
#image: /img/posts/jupyter_icon.png
#bigimg: /img/posts/jupyter_big.png
#gh-repo: michelmetran/package_jupyter
#gh-badge: [follow, star, watch, fork]
#comments: true
---

## Convert Fixed into Dynamic

Criei minhas VMs usando o disco com tamanho fixo, visto que o acesso ao HD virtual fica mais ágil. Contudo, decidi converter em espaço dinâmico, visto que eu teria que transportar essas VMs. Li no artigo [How to Convert Between Fixed and Dynamic Disks in VirtualBox](https://www.howtogeek.com/312456/how-to-convert-between-fixed-and-dynamic-disks-in-virtualbox/) instruções para fazer, conforme segue

```powershell
# No Windows, vai até a pasta de instalação
cd C:\Program Files\Oracle\VirtualBox

# Compacta o Disco da VM do Win
VBoxManage.exe clonemedium disk "C:\Users\michelsilva\VMs\Ubuntu\Ubuntu.vdi" "C:\Users\michelsilva\VMs\Ubuntu\Ubuntu-dynamic2.vdi" -variant Standard

# Compacta o Disco da VM do Ubuntu
VBoxManage.exe clonemedium disk "C:\Users\michelsilva\VMs\Win\Win.vdi" "C:\Users\michelsilva\VMs\Win\Win-dynamic.vdi" -variant Standard
```

<br>

Agora é necessário compactar. Inicialmente faz-se isso:

```powershell
# Compact
VBoxManage.exe modifyhd --compact "C:\Users\michelsilva\VMs\Ubuntu\Ubuntu-dynamic2.vdi"
VBoxManage.exe modifyhd --compact "C:\Users\michelsilva\VMs\Win\Win-dynamic.vdi"
```

<br>

Mas ainda assim o ideal é compactar o Sistema Operacional do host. No Widows, trata-se do desframentador. No Linux é foda!, vários eros.

```bash
systemctl stop systemd-journald.socket
systemctl stop systemd-journald.service
sudo swapoff -a
mount -n -o remount,ro -t ext2 /dev/sda5 /
zerofree /dev/sda5 -v
```

<br>

É possível alterar o tamanho do disco tb.

```powershell
.\VBoxManage.exe modifyhd "E:\VMs\Ubu\Ubuntu\Ubuntu.vdi" --resize 40960
```

<br>

## CloneVDI

Após os comandos, notei que a compactação não foi bem sucesdida.
Com o aplicativo [CloneVDI tool](https://forums.virtualbox.org/viewtopic.php?t=22422) o processo de compactação foi facilitado.

<br>

## Adjust Resolution

- [Getting 1920x1080 resolution or 16:9 aspect ratio on Ubuntu or Linux Mint](https://superuser.com/questions/758463/getting-1920x1080-resolution-or-169-aspect-ratio-on-ubuntu-or-linux-mint)

<br>

## Encriptando Virtual Machine

O Virtual Box possibilita que o disco seja encriptado.
Achei boa opção pois minhas VMs ficam em HDs externos e, se alguém acessa-los, poderá acessar a VM com todos os logins habilitados.

![Encrypt](https://i.imgur.com/ns3c9XH.png)

<br>

## GitHub porta 22

Devido as configurações de proxy do MP, o github não funciona no protocolo ssh, para fazer o push dos repositórios.
Para contornar isso, é necessário alterar a porta padrão do hithub e usar a conhecida 443.

```bash
sudo gedit ~/.ssh/config
```

And I added the following

```
Host github.com
 Hostname ssh.github.com
 Port 443
```

<br>

**Referência**

- https://stackoverflow.com/questions/15589682/ssh-connect-to-host-github-com-port-22-connection-timed-out

<br>

## Remover Dispositivo de rede

<br>

**Referência**

- https://stackoverflow.com/questions/24025256/how-to-disable-a-virtualbox-network-interface-using-a-command-line

<br>

## Keyserver behide proxy

ddddd

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --keyserver-options http-proxy=http://127.0.0.1:3128 --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
```

<br>

**Referências**

- https://unix.stackexchange.com/questions/361213/unable-to-add-gpg-key-with-apt-key-behind-a-proxy

<br>

---

## Atalhos

Em uma tentativa de usar o venv na VM Ubuntu, deu erro: [virtualenv returns error 'Operation not Permitted'](https://stackoverflow.com/questions/28651173/virtualenv-returns-error-operation-not-permitted). Estudando, encontrou soluões

> Error: [Errno 1] Operation not permitted: 'lib' -> '/home/michel/Codes/open_traquitanas/build_classic/venv/lib64'

```bash
python -m venv ./venv
```

```powershell
# No Windows, vai até a pasta de instalação
cd C:\Program Files\Oracle\VirtualBox

# Vê configurações
VBoxManage.exe getextradata "Linux Ubuntu" enumerate

# Habilta symlinks
VBoxManage.exe setextradata "Linux Ubuntu" VBoxInternal2/SharedFoldersEnableSymlinksCreate/"my_codes" 1
```

Não deu certo.
