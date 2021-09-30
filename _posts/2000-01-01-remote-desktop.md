---
title: "Remote Desktop"
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



<!--more-->

### *Ubuntu* para *Windows*

Inicialmente é necessário habilitar a opção de *Área de Trabalho Remota* no Windows 10. Importante ressaltar que essa opção está disponível apenas nas versões do Windows 10 Pro.  A versão Windows Home não possibilita habilitar essa opção, sendo necessário fazer o *upgrade* do Windows.

Usei o aplicativo [Remmina](https://remmina.org/) para se conectar. Observei que o Remmina não aceitou o *hostname*.



### *Windows* para *Ubuntu*


Inicialmente é necessário que o Linux tenha o **xrdp** instalado.

```bash
sudo apt-get install xrdp
```

<br>

Uma vez instalado, basta conectar-se ao Ubuntu, através do Windows, usando o comando ```mstsc```, utilizando o **Executar**.

<br>



### XfreeRDP

Instalar

```bash
sudo apt-get install freerdp2-x11 
```
<br>

Usar

```bash
xfreerdp /multimon /u: <username> /v:<remote windows machine name>
xfreerdp /multimon /u:michel /v:192.168.0.106 -wallpaper
xfreerdp /multimon /u:michel /v:asus-i5-mp
xfreerdp /multimon /gu:workgroup\michel /v:asus-i5-mp
xfreerdp /u:pecege /v:192.168.0.107
```

<br>

Tecla para alternar entre Remote e Host

```
CTRL + ALT + Enter
```

<br>

**Referências**

- [Linux : Remote desktop multiple monitor support](https://medium.com/analytics-vidhya/linux-remote-desktop-multiple-monitor-support-840974e9eb73)
- [Conexão de área de trabalho remota do Windows no Linux com clientes RDP](https://kamarada.github.io/pt/2020/04/11/conexao-de-area-de-trabalho-remota-do-windows-no-linux-com-clientes-rdp/#.XzaSuxlv_AI)
- [**YouTube**: Como Mudar do Windows Home para o Pro, sem Precisar FORMATAR o PC!](https://www.youtube.com/watch?v=uAW83G0Vxis)
- [Como conectar à um servidor Linux via Remote Desktop (Windows)](https://medium.com/@fabianosarmento/como-conectar-%C3%A0-um-servidor-linux-via-remote-desktop-windows-aa5ce95405e8)
- [Como se conectar a partir do Windows no Ubuntu usando o Remote Desktop](https://www.vivaolinux.com.br/dica/Como-se-conectar-a-partir-do-Windows-no-Ubuntu-usando-o-Remote-Desktop)

