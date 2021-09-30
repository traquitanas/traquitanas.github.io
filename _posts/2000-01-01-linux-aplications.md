---
title: "Apps"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package]

#layout: post
#subtitle: Exercícios e Referências
#thumbnail-img: /assets/img/posts/jupyter_icon.png
#cover-img: /assets/img/posts/jupyter_big.png
#share-img: /assets/img/posts/jupyter_big.png
#gh-repo: michelmetran/package_jupyter
#gh-badge: [follow, star, watch, fork]
#comments: true
#language: pt-br

---


# Aplicativos

Iniciei no Ubuntu 18.04 no meio de 2019

[TOC]

<br>

## Internet

Dei preferência pelo comando _apt-get_, pois mantem tudo atualizado sempre.

### Chrome

```bash
# Download
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# Instala
sudo apt install ./google-chrome*.deb
```

<br>

**Referência**

- [How to Install Google Chrome Web Browser on Ubuntu 18.04](https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-ubuntu-18-04/)



### Samba

Ubuntu com Windows

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

https://askubuntu.com/questions/923306/connecting-to-a-windows-network-with-ubuntu-16-04-lts



### Tor

```bash
sudo apt install tor
sudo apt install torbrowser-launcher
```

https://linuxconfig.org/install-tor-proxy-on-ubuntu-20-04-linux

https://linuxconfig.org/how-to-install-tor-browser-on-ubuntu-20-04-lts-focal-fossa-linux



### DropBox

Baixa o pacote

```bash
wget https://www.dropbox.com/download?dl=packages/ubuntu/dropbox_2020.03.04_amd64.deb
```

Instala

```bash
sudo apt install ./dropbox*.deb
sudo apt install python3-gpg
```

<br>

**Referência**

https://linuxhint.com/install_dropbox_debian_10/



### Java

```bash
sudo apt install default-jre
```

Baixa o pacote

https://www.oracle.com/java/technologies/javase-downloads.html

Vai até a pasta de download

```bash
cd ~/Downloads
```

Instala

```bash
sudo apt install ./jdk*.deb
```

**Referências**

https://linuxconfig.org/oracle-java-installation-on-ubuntu-20-04-focal-fossa-linux

### rClone

Serve para montar um driver do OneDrive no PC Linux

**Referências**

https://www.linuxuprising.com/2018/07/how-to-mount-onedrive-in-linux-using.html

### ThunderBird

Remove!

```bash
sudo apt-get remove thunderbird
```

## Manutenção

### TeamViewer

Baixa o pacote

```bash
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
```

Instala

```bash
sudo apt install ./teamviewer*.deb
```

**Referências**

https://www.linuxbabe.com/ubuntu/install-teamviewer-ubuntu-18-04-lts

### Shutter

Adiciona repositório

```bash
sudo add-apt-repository ppa:linuxuprising/shutter
```

Instala

```bash
sudo apt install shutter
```

**Referência**

http://ubuntuhandbook.org/index.php/2019/10/install-shutter-ppa-ubuntu-19-10/



### NVidia

https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04



### MESA Driver

```
sudo add-apt-repository ppa:kisak/kisak-mesa
sudo apt update
sudo apt install mesa
```

https://itsfoss.com/install-mesa-ubuntu/#comments



### Caffeine

```bash
sudo apt-get update && sudo apt-get install caffeine
```



### Gparted

```bash
sudo apt-get update && sudo apt-get install gparted
```



### NeoFetch

```bash
sudo apt-get update && sudo apt install neofetch
```

**Referência**

https://thiagolucioweb.wordpress.com/2017/01/22/neofetch-o-novo-e-melhorado-screenfetch-coloque-o-trademark-bench-do-seu-sistema-no-seu-bash/



## Comunicação

### Kdenlive

**Referência**

[Instalando a versão mais recente do editor de vídeos Kdenlive no Ubuntu](https://www.edivaldobrito.com.br/editor-de-videos-kdenlive-no-ubuntu/)



### Telegram

```bash
sudo add-apt-repository ppa:atareao/telegram
sudo apt-get update && sudo apt-get install telegram
```

**Referência**

https://www.edivaldobrito.com.br/telegram-no-ubuntu-fedora/



### Zoom

**Referência**

https://linuxize.com/post/how-to-install-zoom-on-ubuntu-20-04/



### Teams

Baixar em

https://www.microsoft.com/pt-br/microsoft-365/microsoft-teams/download-app

Vai até a pasta de download

```bash
cd ~/Downloads
```

Instala

```bash
sudo apt install ./teams*.deb
```



### Discord

```bash
sudo apt update && sudo apt install gdebi-core wget
```

```bash
wget -O ~/discord.deb "https://discordapp.com/api/download?platform=linux&format=deb"
sudo gdebi ~/discord.deb
```

**Referência**

https://linuxconfig.org/how-to-install-discord-on-ubuntu-18-04-bionic-beaver-linux



### Skype

```bash
sudo apt install apt-transport-https -y
```

```bash
wget -q -O - https://repo.skype.com/data/SKYPE-GPG-KEY | sudo apt-key add -
```

```bash
echo "deb https://repo.skype.com/deb stable main" | sudo tee /etc/apt/sources.list.d/skypeforlinux.list
```

```bash
sudo apt-get update && sudo apt-get install skypeforlinux
```

**Referência**

https://www.edivaldobrito.com.br/versao-mais-recente-skype-no-linux/



### OBS

```bash
sudo apt install ffmpeg
```

```bash
sudo add-apt-repository ppa:obsproject/obs-studio
```

```bash
sudo apt install ./libfdk*.deb
```

```bash
sudo apt-get update && sudo apt-get install obs-studio
```

**Referência**

https://manjaro.site/how-to-install-obs-studio-on-ubuntu-19-04/

**Problemas**

```bash
glxinfo | grep "OpenGL"
Error: couldn't find RGB GLX visual or fbconfig
```

relatado em https://askubuntu.com/questions/1229941/nvidia-drivers-dont-work-properly-failed-to-load-module-nvidia-module-does

Instalei os drivers Nvidia e deu certo.



### NPM

```bash
sudo apt install npm
```

```bash
npm init
npm install --save react@16.8.6 react-dom@16.8.6 react-scripts@3.0.1
```



### VMare Player

```bash
sudo apt update && sudo apt install build-essential linux-headers-generic
```

```
wget --user-agent="Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0" https://www.vmware.com/go/getplayer-linux
```

```bash
chmod +x getplayer-linux
sudo ./getplayer-linux
```



**Referência**

https://linuxize.com/post/how-to-install-vmware-workstation-player-on-ubuntu-18-04/



### VirtualBox

Instala

```bash
sudo apt install virtualbox
sudo apt remove virtualbox
```

Baixa o pacote

```bash
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -


echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian focal contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

sudo apt update
sudo apt install linux-headers-$(uname -r) dkms
sudo apt-get install virtualbox-6.1

cd ~/
wget https://download.virtualbox.org/virtualbox/6.1.6/Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack
```



**Referências**

https://computingforgeeks.com/how-to-install-latest-virtualbox-on-ubuntu-debian/



#### USB

Para tornar os pendrives disponíveis, após a instalação do Extension Package, é preciso fazer ainda o seguinte comando.

```bash
sudo usermod -aG vboxusers <username>
sudo usermod -aG vboxusers michel
```



**Referência**

https://askubuntu.com/questions/25596/how-to-set-up-usb-for-virtualbox?noredirect=1&lq=1



## Escritório

### Pandoc

```bash
sudo apt-get install pandoc
```



### LaTex

não consegui instar "texlive-generic-recommended" em 20.04

```bash
sudo apt-get install texlive-xetex
sudo apt-get install texlive-fonts-recommended
sudo apt-get install texlive-generic-recommended
sudo apt-get install texlive-plain-generic
```



**Referências**

https://linuxconfig.org/install-virtualbox-on-ubuntu-20-04-focal-fossa-linux



### LaTex

```bash
sudo apt-get install texmaker
```



**Referência**

https://milq.github.io/install-latex-ubuntu-debian/



### Chrome Driver

Para integrar com o Selenium

```bash
sudo apt-get install chromium-chromedriver
```



**Referência**

https://askubuntu.com/questions/1004947/how-do-i-use-the-chrome-driver-in-ubuntu-16-04



### Firefox Driver (GeckoDriver)

```bash
wget https://github.com/mozilla/geckodriver/releases/download/v0.29.1/geckodriver-v0.29.1-linux64.tar.gz
```

```bash
sudo sh -c 'tar -x geckodriver -zf geckodriver-v0.29.1-linux64.tar.gz -O > /usr/bin/geckodriver'
```

```bash
sudo chmod +x /usr/bin/geckodriver
```

```bash
rm geckodriver-v0.29.1-linux64.tar.gz
```



**Referência**

https://askubuntu.com/questions/870530/how-to-install-geckodriver-in-ubuntu



### PhantonJS

First, install or update to the latest system software.

```bash
sudo apt-get update
sudo apt-get install build-essential chrpath libssl-dev libxft-dev
```

Install these packages needed by PhantomJS to work correctly.

```bash
sudo apt-get install libfreetype6 libfreetype6-dev
sudo apt-get install libfontconfig1 libfontconfig1-dev
```

Get it from the [PhantomJS website](http://phantomjs.org/).

```bash
cd ~
export PHANTOM_JS="phantomjs-2.1.1-linux-x86_64"
wget https://bitbucket.org/ariya/phantomjs/downloads/$PHANTOM_JS.tar.bz2
sudo tar xvjf $PHANTOM_JS.tar.bz2
```

Once downloaded, move Phantomjs folder to `/usr/local/share/` and create a symlink:

```bash
sudo mv $PHANTOM_JS /usr/local/share
sudo ln -sf /usr/local/share/$PHANTOM_JS/bin/phantomjs /usr/local/bin
```

Now, It should have PhantomJS properly on your system.

```bash
phantomjs --version
```



**Referência**

https://gist.github.com/julionc/7476620



### 7-zip

http://ubuntuhandbook.org/index.php/2018/10/p7zip-desktop-available-install-ubuntu-18-04/



### Typora

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
sudo apt-get install typora
```



**Referência**

- [Install Typora on Linux](https://support.typora.io/Typora-on-Linux/)



### OCRmyPDF

```bash
sudo apt install ocrmypdf
```



### Tesseract-OCR

Instalar

```bash
sudo apt-get install tesseract-ocr
```

Error opening data file /usr/share/tesseract-ocr/4.00/tessdata/por.traineddata

Please make sure the TESSDATA_PREFIX environment variable is set to your "tessdata" directory.

Failed loading language \'por\' Tesseract couldn't load any languages!

Could not initialize tesseract.

Download

```bash
wget https://github.com/tesseract-ocr/tessdata/raw/master/por.traineddata
```

Move

```bash
sudo mv -v por.traineddata /usr/share/tesseract-ocr/4.00/tessdata/
```

Download

```bash
wget https://github.com/tesseract-ocr/tessdata/raw/master/eng.traineddata
```

Move

```bash
sudo mv -v eng.traineddata /usr/share/tesseract-ocr/4.00/tessdata/
```

### Steam

```bash
wget http://repo.steampowered.com/steam/archive/precise/steam_latest.deb
```

```bash
sudo dpkg -i steam_latest.deb
```

```bash
sudo apt-get install -f
```

**Referências**

https://www.edivaldobrito.com.br/cliente-steam-no-ubuntu/



### Certificado Digital

```
opensc-tool --list-readers
```

```
pcsc_scan
```

```
sudo dpkg -i safe*.deb
```

Segui isso aqui!!!!!

http://www.guicolandia.net/peticionamento-eletr%C3%B4nico-no-ubuntu-20-04.html

https://extpose.com/ext/61522

https://www.linkedin.com/in/fl%C3%A1vio-nascimento-323a42ab/



## Mídia

### Spotify

Adiciona chaves

```bash
curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | sudo apt-key add -
```

Adiciona repositórios

```bash
echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
```

Instala

```bash
sudo apt-get update && sudo apt-get install spotify-client
```

**Referência**

https://www.spotify.com/br/download/linux/



### InkScape

Adiciona Repositório

```bash
sudo add-apt-repository ppa:inkscape.dev/stable
```

```bash
sudo apt-get update && sudo apt-get install inkscape
```

**Referências**

http://ubuntuhandbook.org/index.php/2019/01/inkscape-0-92-4-released-install-ubuntu-18-04/



### Conky

Instala

```bash
sudo apt-get install conky && sudo apt-get install conky-all
```

Aplicativo

```bash
conky
```

Configuração do

```bash
/home/michel/.conkyrc
/etc/conky/conky.conf
```

**Referências**

https://vitux.com/how-to-install-conky-system-monitor-and-conky-manager-on-debian-10/



### VLC

```bash
sudo snap install vlc
```

**Referência**

https://www.vlchelp.com/install-ubuntu-linux/



### Kodi

```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
```

**Referência**

https://www.youtube.com/watch?v=ZLVLUBWLQts

https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux



## Geoprocessamento

### QGIS

Editar o arquivo

```bash
sudo gedit /etc/apt/sources.list
```

Adicionar

```bash
deb [ arch=amd64 ] https://qgis.org/ubuntu-ltr focal main
deb-src [ arch=amd64 ] https://qgis.org/ubuntu-ltr focal main
```

Instalar

```bash
sudo apt-get update && sudo apt-get install qgis qgis-plugin-grass
```

**Referências**

https://qgis.org/pt_BR/site/forusers/alldownloads.html#debian-ubuntu

https://linuxhint.com/install-qgis3-geospatial-ubuntu/



### FileGDB API

Baixa o pacote (# não deu certo, fiz o download manualmente)

```bash
wget https://github.com/Esri/file-geodatabase-api/blob/master/FileGDB_API_1.5/FileGDB_API_1_5_64.tar.gz
```

```bash
# Vai para a pasta do Dowload
cd Downloads

# Descompacta
tar -zxvf FileGDB_API*.tar.gz

# Move
sudo mv FileGDB_API-64*/ /opt/

# Acessa
cd /opt/FileGDB_API-64*

#
export LD_LIBRARY_PATH=`pwd`/lib
cd samples
make
#sudo cp ../lib/* /usr/local/lib
sudo ldconfig

# ddd
which gdalinfo

# repar
sudo mv /usr/local/lib/lib* /home/michel/


# Tá no README do unzip
sudo apt-get install freeglut3-dev

# Deleta
sudo rm -r /opt/FileGDB_API-64
```

```bash
echo '/opt/FileGDB_API-64gcc51/lib' > /etc/ld.so.conf
sudo gedit /etc/ld.so.conf
```

Instala

```bash
echo "export FileGDB_HOME=/opt/FileGDB_API-64" >> ~/.bashrc

# Referências
# https://geodacenter.github.io/setup-esri-fgdb.html
```

```bash
./configure --with-fgdb=/opt/FileGDB_API-64
make
make install
```

https://trac.osgeo.org/gdal/wiki/FileGDB

https://gis.stackexchange.com/questions/292506/how-do-i-install-esri-file-gdb-api-in-ubuntu-16-04-so-qgis-2-8-can-see-it

https://wiki.wildsong.biz/index.php/Building_GDAL_on_Linux#ESRI_file_geodatabases

```bash
ogrinfo --formats|sort
```

**Referências**

https://askubuntu.com/questions/1087150/install-gcc-5-on-ubuntu-18-04

https://github.com/Esri/file-geodatabase-api/tree/master/FileGDB_API_1.5.1

https://proceedings.esri.com/library/userconf../devsummit18/papers/dev-int-208.pdf

### Outros

```bash
sudo apt install build-essential libglvnd-dev pkg-config
```

Listar todos os programas

```bash
sudo apt-get install aptitude
aptitude -F' * %p -> %d ' --no-gui --disable-columns search '?and(~i,!?section(libs), !?section(kernel), !?section(devel))'
```



### Codecs

```bash
sudo apt update
sudo apt install libdvdnav4 libdvd-pkg gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg ubuntu-restricted-extras
```

```bash
sudo dpkg-reconfigure libdvd-pkg
```

<br>

**Referências**

https://websiteforstudents.com/how-to-enable-ubuntu-18-04-lts-beta-to-play-videos-files/



### Google Earth

```bash
wget https://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb -O google-earth-stable.deb
```

```
sudo dpkg -i google-earth-stable.deb
```

**Referência**

- [Como instalar o Google Earth no Ubuntu, Debian e derivados](https://www.edivaldobrito.com.br/google-earth-no-ubuntu/)



## Códigos

### IDE IntelliJ IDEA

instala via snap

```bash
# Para Instalar
sudo snap install intellij-idea-community --classic

# Para Atualizar
sudo snap refresh intellij-idea-community
```

<br>

**Referência**

- [Como instalar a incrível IDE Java IntelliJ IDEA no Linux](https://www.edivaldobrito.com.br/ide-intellij-idea-no-ubuntu-debian/)



### R

```bash
sudo apt install apt-transport-https software-properties-common
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'

sudo apt update && sudo apt install r-base
```

Para sair de qualquer sessão, basta apertar:

```
q()
quit()
```

<br>

**Referência**

- [How to Install R on Ubuntu 18.04](https://linuxize.com/post/how-to-install-r-on-ubuntu-18-04/)



### R Studio

```
sudo apt update
sudo apt install r-base gdebi-core
sudo apt install gdebi-core
```



```
wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.4.1106-amd64.deb
sudo gdebi rstudio*.deb
sudo apt install ./rstudio*.deb
sudo apt install libclang-dev
```

<br>

**Referências**

- [Unable to install libclang on 20.04 LTS](https://askubuntu.com/questions/1337617/unable-to-install-libclang-on-20-04-lts)

  

### VsCode

```bash
sudo apt update && sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update && sudo apt install code
```

https://linuxize.com/post/how-to-install-visual-studio-code-on-ubuntu-18-04/



### VIM

Instalei o VIM seguindo https://www.simplified.guide/ubuntu/install-vim

Sair do VIM é ESC e :qw

https://stackoverflow.com/questions/11828270/how-do-i-exit-the-vim-editor



### Draw.io

```
sudo snap install drawio
```

https://snapcraft.io/install/drawio/ubuntu



### XAMPP

```
wget "https://sourceforge.net/projects/xampp/files/XAMPP%20Linux/7.4.8/xampp-linux-x64-7.4.8-0-installer.run/download" -O xampp-installer.run

chmod +x xampp-installer.run
sudo ./xampp-installer.run

echo -e '[Desktop Entry]\n Version=1.0\n Name=xampp\n Exec=gksudo /opt/lampp/manager-linux-x64.run\n Icon=/opt/lampp/icons/world1.png\n Type=Application\n Categories=Application' | sudo tee /usr/share/applications/xampp.desktop
```

Para possibilitar alteração de arquivos

```
sudo chown -R michel:michel /opt/lampp/htdocs
```

```
sudo cp -r /home/michel/Documents/Arquivos/Downloads/curriculo /opt/lampp/htdocs
```

https://www.edivaldobrito.com.br/como-instalar-o-xampp-no-linux/

https://askubuntu.com/questions/942488/xampp-apache-web-server-stopped-ubuntu
