---
title: "Conda"
date: 2019-01-00T00:00:00-03:00
last_modified_at: 2022-06-28T00:00:00-03:00
excerpt_separator: "<!--more-->"
tags: [conda]
categories: [mpsp]
---

Ao tentar criar um enviroment no conda, na rede institucional, recebia o seguinte erro:

> CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://repo.anaconda.com/pkgs/main/win-64/current_repodata.json>

<br>

Estudando o problema, encontrei uma solução preliminar no [StackOverflow](https://stackoverflow.com/questions/42563757/conda-update-condahttperror-http-none), que sugere que seja removido a verificação do ssl.

```bash
conda config --set ssl_verify no
```

Sabemos das implicações de fazer isso, porém é a única alternativa encontrada no momento.
