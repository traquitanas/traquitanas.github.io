---
title: Rename Files
#layout: post
#subtitle: Exercícios e Referências
#tags: [python, pycharm, jupyter, package]
#image: /img/posts/jupyter_icon.png
#bigimg: /img/posts/jupyter_big.png
#gh-repo: michelmetran/package_jupyter
#gh-badge: [follow, star, watch, fork]
#comments: true

---



Códigos necessários para renomear arquivos

```bash
rename 's/Nota de Corretagem //' *.pdf
rename 's/-/./' *.pdf
rename 's/-/./' *.pdf
rename 's/\.pdf$//' *.pdf
rename 's/(.*)/$1 - Nota.pdf/' *
```



Se for renomear fotos usando o Exit

```bash
exiftool -fileOrder DateTimeOriginal -recurse -extension jpg -extension  jpeg -ignoreMinorErrors '-FileName<CreateDate' -d "%Y.%m.%d -  %H.%M.%S %%c".%%le ~/Documents/Andre/
```


