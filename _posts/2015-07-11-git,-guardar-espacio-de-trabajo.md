---
layout: post
title: Git, guardar espacio de trabajo
tags: git tips more
eye_catch: ""
---

Siempre que compartes un repo con otras personas, sabes que te encontrarás con los bonitos merges caóticos.
Como truco para no perder nada y tener en local todo actualizado justo antes de subir mis cambios yo almaceno todo mi estado
 (del working directory) con un stash.

## El tema sería el siguiente:

* Estamos dos personas en la misma rama
* Cada uno desarrolla
* El otro sube sus cambios sin problemas
* LLego yo a subir lo mío y no estoy actualizada
* Me guardo mis cambios
 

```
$ git stash
```

* Me descargo lo que hay arriba

```
$ git pull
```

* Recupero mis cambios

```
$ git stash pop
```

* Agrego mis cambios y describo mi commit

```
$ git add --all
git commit -m "Mis cambios automágicos"
```

* Subo mi commit

```
$ git push
```

Y todo perfecto, no he visto asomar la cabeza a ningún merge!!
