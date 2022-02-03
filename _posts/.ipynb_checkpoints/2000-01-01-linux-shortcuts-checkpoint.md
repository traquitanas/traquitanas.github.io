---
title: "Shortcuts"
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

O Ubuntu possibilita a criação de teclas de atalho que facilitam o uso do PC. Além de atalhos para programas, é possível uma infinidade de possibilidades com as teclas de atalho.

Como uso muito códigos em *python*, que quero roda-los várias vezes ao dia, por exemplo, é possível colocar o código de *python* na tecla de atalho.



### Applications

Adicionar tecla de atalho para o Terminal (equivalente do cmd)

```bash
gsettings get org.gnome.settings-daemon.plugins.media-keys terminal
gsettings set org.gnome.settings-daemon.plugins.media-keys terminal "['<Super>r']"
```

<br>

Adicionar tecla de atalho para o Nautilus (equivalente do Windows Explorer)

```bash
gsettings get org.gnome.settings-daemon.plugins.media-keys home
gsettings set org.gnome.settings-daemon.plugins.media-keys home "['<Super>e']"
```

<br>

Adicionar programa que se abre na linha de comando

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "'spotify'"
```



### Custom Shortcuts

Inicialmente é necessário "criar" um custom keybinds (custom0, custom1, custom2...)

```bash
gsettings get org.gnome.settings-daemon.plugins.media-keys custom-keybindings
gsettings set org.gnome.settings-daemon.plugins.media-keys custom-keybindings "['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/']"

gsettings set org.gnome.settings-daemon.plugins.media-keys custom-keybindings "['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/']"
```

<br>

Adicionar tecla de atalho para o Terminal (equivalente do cmd)

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/ name "'hotmilhas'"
```

<br>

E agora é possível atribuir uma tecla de atalho

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ binding "'<Super>j'"

gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/ binding "'<Super>k'"
```

<br>

### Bash

Adicionar *script*, abrindo o terminal

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "gnome-terminal -- bash -c '$HOME/Documents/Sourcecode/open_dsa/linguagem/sh/open_jn.sh ; bash'"

gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/ command "gnome-terminal -- bash -c '$HOME/Documents/Sourcecode/open_dsa/linguagem/sh/convert_jn.sh $HOME/Documents/Sourcecode/case_office/jupyter_notebook/hello.ipynb; bash'"

gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/ command "gnome-terminal -- bash -c '$HOME/Documents/Sourcecode/open_dsa/linguagem/sh/convert_jn.sh $HOME/Documents/Sourcecode/open_cash/hotmilhas/hotmilhas.ipynb; bash'"
```

<br>

Adicionar *script*, sem abrir o terminal. Não deu certo. Preciso testar mais.

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "'$HOME/Documents/Sourcecode/my_linux/sh/open_jn.sh'"
```

<br>

### Command

Roda *command* bash com visualização
```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "gnome-terminal -- bash -c 'echo Monkey; read line'"
```

<br>

### Python

Roda *script* python sem visualização

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "gnome-terminal -- python3 $HOME/Documents/Sourcecode/my_knowledge/linguagem/python/test.py"
```

<br>

Roda *script* python com visualização

```bash
gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "gnome-terminal -- bash -c 'python3 $HOME/Documents/Sourcecode/my_knowledge/linguagem/python/test.py; read line'"
```

