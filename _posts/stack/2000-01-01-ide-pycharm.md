---
title: "IDE: PyCharm"
excerpt_separator: "<!--more-->"
tags: [linux, git, github, gitpages, python, pycharm, anaconda, miniconda]

#layout: post
#subtitle: Escrevendo scripts Python com auxílio do PyCharm, Miniconda e Jupyter
#thumbnail-img: /assets/img/posts/py_icon.png
#share-img: /assets/img/posts/py_big.png
#cover-img: /assets/img/posts/py_big.png
#comments: true
#language: pt-br

---

O **<a title="Link do PyCharm" href="https://www.jetbrains.com/pycharm/" target="_blank">PyCharm</a>** é um ambiente de desenvolvimento integrado (ou IDE, do inglês '_Integrated Development Environment_') usado em programação de computadores, especificamente para a linguagem **<a title="Link do Python" href="https://www.python.org/" target="_blank">Python</a>**.

<!--more-->

{: .box-warning}
**Aviso:** Esse _post_ tem a finalidade de mostrar os comandos básicos e me deixar com uma "cola" rápida para meu uso cotidiano. Todas os códigos são exemplificativos e podem/devem ser alterados, indicando o nome dos arquivos e diretórios corretamente.

<br>

### Instalando o *PyCharm Community* no Ubuntu

Executei os procedimentos detalhados em aqui [How to Install PyCharm on Ubuntu 18.04](https://linuxize.com/post/how-to-install-pycharm-on-ubuntu-18-04/).

Simplificando ao máximo, basta aplicar o comando abaixo no terminal.

```bash
sudo snap install pycharm-community --classic
```

[Conda Enviroments with Jupyter Notebooks Kernels](https://www.youtube.com/watch?v=Ro9l0eapoJU)

<br>

### Instalando o *PyCharm Professional* no Ubuntu

```bash
sudo snap install pycharm-professional --classic
```

<br>

### JetBrains ToolBox


```bash
# Faz Download
wget -O ~/Downloads/jetbrains.tar.gz "https://download.jetbrains.com/toolbox/jetbrains-toolbox-1.22.10774.tar.gz"

# Descompacta
cd ~/Downloads
tar -zxvf jetbrains.tar.gz

# Instala
cd jetbrains-toolbox*
./jetbrains-toolbox
```

https://www.youtube.com/watch?v=gZ_XtkcPSHY

<br>

### IDE IntelliJ IDEA

instala via snap

```bash
# Para Instalar
sudo snap install intellij-idea-community --classic

# Para Atualizar
sudo snap refresh intellij-idea-community
```

<br>

### Problem: Inotify

Para ajustar a mensagem constantemente recebido, referente ao tempo adotado pelo **inotify**, contrei uma [referência](https://youtrack.jetbrains.com/articles/IDEA-A-2/Inotify-Watches-Limit) que explica como resolver. VIsando automaticar a questão, basta rodar o código abaixo na linha de comando e reiniciar o PyyCharm. *Done!*

```bash
echo "# Inotify on PyCharm" | sudo tee -a /etc/sysctl.d/idea.conf && \
echo "# https://youtrack.jetbrains.com/articles/IDEA-A-2/Inotify-Watches-Limit" | sudo tee -a /etc/sysctl.d/idea.conf && \
echo "" | sudo tee -a /etc/sysctl.d/idea.conf && \
echo "fs.inotify.max_user_watches = 524288" | sudo tee -a /etc/sysctl.d/idea.conf && \
sudo sysctl -p --system
```


**Referência**

- [Como instalar a incrível IDE Java IntelliJ IDEA no Linux](https://www.edivaldobrito.com.br/ide-intellij-idea-no-ubuntu-debian/)
