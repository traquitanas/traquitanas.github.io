---
title: "Requirements"
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

O arquivo *requirements.txt*, usualmente localizado na pasta-raiz do projeto, tem a finalidade de listar quais são os *packages* que foram utilizados naquele determinado projeto.

<!--more-->

Muitas vezes, no curso de um *script*, é possível instalar uma dependência utilizando o ```pip install {nome do pacote}```, porém o arquivo *requirements.txt* se faz fundamental quando os projetos serão acessados por aplicações, tais como ***Django***, ***Flask***, ***Heroku*** e ***MyBinder***, por exemplo, sendo esse o motivo principal para criar esse arquivo.



### *Pip Freeze*

O comando ```pip freeze``` é o mais difundido na internet para se criar o arquivo *requirements.txt*, ou seja, o arquivo com o qual é possível indicar quais os *packages* necessários para rodar um determinado *script*. O problema é que **ele não lista apenas** os *packages* utilizados em um determinado *script*, listando **TODOS** os *packages* de instalados no *python* (ou ambiente *python*).

Particularmente eu utilizo *enviroments* do Conda, com dezenas de pacotes instalados em cada *enviroments*, e os arquivos *requirements.txt* ficavam muito extensos, apresentando alguns problemas.

```python
#pip freeze > requirements.txt
```



### *Pipreqs*

O pacote [**pipreqs**](https://pypi.org/project/pipreqs/), pelas descrições, pareceu atender a demanda de lista **APENAS** os pacotes de um determinado projeto. Porém ele não funciona diretamente no *Juptyter Notebook*, motivo que foi preciso inserir um ponto de exclamação no início do comando, para que o *jupyter* interpretasse que se trata de um comando a ser feito em *bash*.

```python
!pipreqs '.' --force --debug --print
```



### *Environment.yml*

Descobri ainda que o comando ``` conda env export > environment.yml``` pode auxiliar na criação destes parâmetros, não sendo exatamente o que se busca, ou seja, o arquivo *requirements.txt* necessário para aplicações.

```python
#!conda env export > environment.yml
```

