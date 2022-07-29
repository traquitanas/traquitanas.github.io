---
title: "PowerShell"
date: 2019-06-13T15:34:30-04:00
last_modified_at: 2022-06-29T00:00:00-03:00
#date: 2019-01-00T00:00:00-03:00
#last_modified_at: 2022-06-28T00:00:00-03:00
excerpt_separator: "<!--more-->"
categories: [apps]
tags: [python, pycharm, jupyter, package]
#subtitle: Exercícios e Referências
#layout: post
#image: /img/posts/jupyter_icon.png
#bigimg: /img/posts/jupyter_big.png
#gh-repo: michelmetran/package_jupyter
#gh-badge: [follow, star, watch, fork]
#comments: true
---


Sempre que abria o PowerShell, recebia um alerta sobre atualização. Utilizando o comando abaixo, no PowerSheel 6, é possível atualizar (rodar como admin) para o PS7, conforme explicado, em detalhes, no artigo [How to Install and Update PowerShell 6](https://www.thomasmaurer.ch/2019/03/how-to-install-and-update-powershell-6/).

```powershell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```
