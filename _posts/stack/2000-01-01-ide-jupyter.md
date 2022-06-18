---
title: "IDE: Jupyter Notebook e Jupyter Lab"
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

O **<a title="Link do Projeto Jupyter" href="https://jupyter.org/" target="_blank">Projeto Jupyter</a>** existe para desenvolver software de código aberto, padrões abertos e serviços para computação interativa em dezenas de linguagens de programação.

<!--more-->

Um **<a title="Link do Notebook Jupyter" href="https://hub.gke.mybinder.org/user/ipython-ipython-in-depth-6b7gwnpm/notebooks/binder/Index.ipynb" target="_blank">Notebook Jupyter</a>** é um ambiente computacional web para a internet rica para criação de documentos para a plataforma **Jupyter**. O termo _"notebook"_ pode, dependendo do contexto, fazer referência a entidades distintas como **Jupyter** (aplicativo _Web_), **Jupyter Python** (servidor _Web_) ou ao formato de documento para a plataforma.

Um documento **Jupyter Notebook** é estruturado formato JSON, contendo uma lista ordenada de células de entrada/saída que podem conter código, texto (usando **Markdown**), matemática, gráficos e texto enriquecido, geralmente terminando com a extensão _".ipynb"_.

### _Jupyter Notebook_

Os procedimentos foram adaptados d'um vídeo intitulado _Conda Enviroments with Jupyter Notebooks Kernels_[^4].
Basta instalar os _packages_ abaixo **ou**...

```bash
conda install jupyter
conda install nb_conda
conda install ipyparallel
```

... ou ainda, criar um ambiente que contenha eles, sendo essa opção mais recomendada.

```bash
conda create --name pablocarreira jupyter nb_conda ipyparallel pandas geopandas		# Criar ambiente
```

Após isso basta inserir o seguinte comando no terminal que um servidor será iniciado e, por meio do navegador, você poderá editar seus arquivos com extensão _".ipynb"_.

```bash
jupyter notebook
```

### _Jupyter Lab_

```bash
jupyter lab
```
