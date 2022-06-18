---
title: "Virtual Box: Instalação"
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

# Windows Host | Ubuntu Guest

<br>

## Compartilhando pasta entre _host_ e _guest_

Para compartilhar pastas entre o _host_ e o _guest_ é necessário configurar as pastas a serem compartilhas:
Windows Host | Ubuntu Guest

![image.png](https://i.imgur.com/WYtxNTy.png)

Ainda, no _guest_, é necessário adicionar o usuário definido no grupo do _vsboxsf_ com o seguinte comando:

```bash
sudo adduser $USER vboxsf
```

_TODO_: Notei que o problema de se compartilhar arquivos que estão na nuvem da _microsoft_ é que a função _on demand_ deixa de funcionar. O VBOX passa a fazer o download de todos os arquivos.

<br>

**Referência**

- https://askubuntu.com/questions/890729/this-location-could-not-be-displayed-you-do-not-have-the-permissions-necessary

<br>

## Compartilhando pasta entre _host_ e _others devices_

Cenário: uma vez com a virtual machine funcionando, criei um hotspot móvel para conectar outros dispositivos externos a rede que estão inserido.

Uma vez que criei uma rede secundária, posso "montar" unidades dentro da minha _virtual box_.
No caso eu estava no pc do trabalho (_windows_), com um ubuntu em uma _virtual machine_ (guest).

No Ubuntu eu me conectei ao meu notebook (ubuntu), por wi-fi, via hotspot. E queria montar unidades.
Na virtual machine é necessário ter os pacotes necessários para motar unidades em outros sistemas de arquivos (diferentes do ext4).

```
sudo apt install nfs-common
sudo apt install cifs-utils
```

Identificar o IP dos dispositivos conectados pelo hotspot móvel.

```
arp -a
```

Montar

```
sudo mount -t cifs //10.42.0.168/Geodata/Sourcecode /home/michel/Documents/Geodata-i7 -o username=michel
sudo mount -t cifs //10.42.0.168/Geodata /home/michel/Documents/Geodata-i7 -o uid=1000,username=michel,password=*****
```

Desmontar

```
sudo umount  -f -l /home/michel/Documents/Geodata-i7
```

<br>

**Referência**

- https://askubuntu.com/questions/525243/why-do-i-get-wrong-fs-type-bad-option-bad-superblock-error
- https://askubuntu.com/questions/506110/listing-devices-connected-in-hotspot-through-terminal

<br>

---

https://gist.github.com/kentwait/ea49b270f4f7480541409c5ded093ec9
https://askubuntu.com/questions/161759/how-to-access-a-shared-folder-in-virtualbox

# Configura o ponto de pontantagem com um nome diferente... e sem habilitar nada!

# Deu certo!

sudo mount -t vboxsf my_codes ~/Codes
sudo mount -t vboxsf -o uid=1000,gid=1000 my_codes ~/Codes

# Comando que vê o que está montado!

df

# Desmonta!

sudo umount my_codes

# Uma vez que, manualmente, deu certo a montagem!

sudo gedit /etc/fstab

my_codes /home/michel/Codes vboxsf defaults,uid=1000,gid=1000,umask=0022 0 0

sudo gedit /etc/modules

vboxsf

https://gist.github.com/kentwait/ea49b270f4f7480541409c5ded093ec9
