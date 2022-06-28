---
title: "Bluetooth"
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

Inicialmente encontrar os dispositivos conectados

```bash
pactl list | grep -Pzo '.*bluez_card(.*\n)*'
```

É possível ver que a latência é de zero. Vamos alterar essa configuração!

```bash
# Comando Padrão
pactl set-port-latency-offset <NAME> <PORT> <BUFFER_SIZE_MICROSECONDS>

# Comando Ajustado com as variáveis!
pactl set-port-latency-offset bluez_card.E8_07_BF_01_4D_CD headset-output 50000
```

<br>

Reiniciar o _bluetooth_

```bash
sudo service bluetooth restart
```

<br>

**Referências**

- [A2DP on PulseAudio - terrible choppy/skipping audio](https://askubuntu.com/questions/475987/a2dp-on-pulseaudio-terrible-choppy-skipping-audio)

- https://askubuntu.com/questions/589885/automatically-switch-sound-output-device-to-bluetooth-headset-force-to-a2dp-pr
- https://sandalov.org/blog/2146/
