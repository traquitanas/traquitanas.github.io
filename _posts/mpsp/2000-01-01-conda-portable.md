---
title: "Conda"
excerpt_separator: "<!--more-->"
tags: [linux, git, github, gitpages, python, pycharm, anaconda, miniconda]
---

Ao tentar criar um enviroment no conda, na rede institucional, recebia o seguinte erro:

> CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://repo.anaconda.com/pkgs/main/win-64/current_repodata.json>

<br>

Estudando o problema, encontrei uma solução no [StackOverflow](https://stackoverflow.com/questions/42563757/conda-update-condahttperror-http-none), que sugere que seja removido a verificação do ssl.

```
conda config --set ssl_verify no
```
