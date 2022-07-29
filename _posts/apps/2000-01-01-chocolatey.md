---
title: "Chocolatey"
date: 2019-06-13T15:34:30-04:00
last_modified_at: 2022-06-28T11:00:00-03:00
excerpt_separator: "<!--more-->"
categories: [apps]
#tags: [python, pycharm, jupyter, package, pandas]
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

Nunca gostei de instalar aplicativos no Windows. É uma tarefa chata, após cada formatação (nos PCs pessoais, de amigos e família), era necessário acessar cada _site_ do aplicativo, fazer o _download_, e instalar.

Para facilitar essa etapa, eu costumava ter uma pasta de executáveis (arquivos _.exe_) para instalar os aplicativos. Os arquivos executáveis usualmente grandes, ocupavam bastante espaço em um HD e, frequentemente, estavam desatualizados!

Quando passei a usar o Ubuntu, vi o quão fácil é instalar um aplicativo por meio de uma linha de comando. Achava mágico, com um simples comando `sudo apt install code`, ter o editor VsCode instalado no meu PC, por exemplo.

<!--more-->

Essa facilidade me fez buscar usar e aprender aplicativos que sejam de fácil instalação e manutenção. Com isso, passei a usar/buscar projetos _freeware_, que não dependessem de pirataria, _cracks_, _patchs_, _keygens_ os quais, além de dependerem de ajustes manuais, também contribuem (e muito!) para aumentar a vulnerabilidade dos PC.

Ainda assim, a facilidade proporcionada pelo gerenciador de pacotes `apt` limitava-se ao meu Debian/Ubuntu. Contudo, muitos PCs que uso tem sistema operacional Windows e eu ficava transtornado com a dificuldade de manter aplicativos instalados e atualizados em comparação ao Ubuntu. Nesse contexto que conheci o [Chocolatey.org](https://chocolatey.org/), um gerenciador de pacotes para Windows!

Com ele é possível instalar várias aplicações por meio de linhas de comando e mante-las atualizadas! Aprendi alguns passos básicos ao ler o artigo [How to install chocolatey/choco on Windows 10](https://jcutrer.com/windows/install-chocolatey-choco-windows10).

<br>

---

## Instalando o Choco

```powershell
# Instala
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

<br>

---

## Comandos Básicos

```powershell
# Help
choco -?

# Procurar pacote
choco search hugo

# Atualizar Choco
choco upgrade chocolatey

# Atualiza tudo
choco upgrade all -y

# Lista pacotes instalados pelo choco
choco list --local-only
```

<br>

---

## Instalando Aplicativos

Abaixo listei os aplicativos que eu uso, porém existem muito outros [_packages_](https://community.chocolatey.org/packages) disponíveis.

```powershell
# Internet
choco install firefox -y
choco install chrome
choco install jre8 -y

# Office
choco install notepadplusplus.install -y
choco install adobereader -y
choco install office365business -y
choco install 7zip.install -y

# Comunicação
choco install microsoft-teams.install -y
choco install teamviewer -y
choco install zoom -y

# Codes
choco install vscode -y
choco install jetbrainstoolbox -y
choco install git.install -y
choco install filezilla -y
choco install miniconda3 -y
choco install miniconda3 --params="'/AddToPath:1'" -y
choco install microsoft-windows-terminal -y
choco install dotnetfx -y
choco install vcredist140 -y
choco install tableau-public -y

# Mídia
choco install vlc -y
choco install spotify -y
choco install inkscape -y

# Manutenção
choco install ccleaner -y
choco install treesizefree -y
```
