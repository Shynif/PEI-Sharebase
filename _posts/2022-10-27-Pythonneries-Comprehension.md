---
layout: post
title: "Pythonneries: Listes par compréhension"
date: 2022-10-27
image: '/assets/img/'
description: 'Listes, Dictionnaires, Sets et Tuples en 1 ligne !'
main-class: 'python'
color: '#4B8BBE'
tags:
- python
- code golf
introduction: 'Listes, Dictionnaires, Sets et Tuples en 1 ligne !'
---

# Introduction

Particularité de Python, il est possible d'écrire des listes, tuples et dictionnaires *en seulement une seule ligne*.
Une écriture plus rapide, parfois plus lisible et surtout très élégante lorsque l'on fait de la programmation fonctionelle.
Cette fonctionnalité n'est pas forcément très importante mais elle peut vous surprendre.

# Les bases

## Introduction de la solution

Imaginons que nous voulons une liste nommé `nombres` contenant tout les entiers allant de 0 à 9 (inclus).<br>
La première méthode est simple et acamédique :

```py
nombres = []
for i in range(10) :
    nombres.append(i)

# Valeur de 'nombres' : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Mais ça prend **beaucoup** de place et de temps à écrire. Sans parler de la complexité de relecture du code.<br>
Encore pire pour les amoureux de programmation fonctionnelle : **nous créons une variable pour stocker la liste !**

Reproduisons le même exercice avec une **Liste par compréhension**.

```py
nombres = [i for in range(10)]

# Valeur de 'nombres' : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# print( [i for in range(10)] )     Parfois même plus besoin de la variable 'nombres' selon notre utilisation !
# return [i for in range(10)]
```

Beaucoup plus simple et "lisible" quand on connaît le sens de lecture.

## Struture et sens de lecture

Nous allons voir comment écrire une liste par compréhension.<br>
**[** **valeur ajoutée à la liste** <u>boucle</u> **condition d'ajout** **]**

Par exemple :<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **i** <u>for i in range(100)</u> **if i%2==0** ]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valeur ajoutée à la liste : **i**<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;boucle : <u>for i in range(100)</u><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;condition d'ajout : **if i%2==0**

L'exemple reprend simplement le code :
```py
liste = []
for i in range(100) :        # boucle
    if i%2==0 :              # condition d'ajout
        liste.append( i )    # valeur ajoutée à la liste
```

Je vous conseil d'essayer vous-même et de vous entraînez avec ce style d'écriture pour mieux comprendre, visualiser et mémoriser.

# Dictionnaires, Set et Tuples par compréhension

Si vous avez compris les listes par compréhension il n'y a rien de sorcier.

## Dictionnaire et Set par compréhension

Pour les **Dictonnaires** la syntax est :<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**{** **clé:valeur** `boucle` **condition d'ajout** **}**

Pour les **Sets** la syntax est :<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**{** **valeur ajoutée** `boucle` **condition d'ajout** **}**

Exemples :
```py
# Dico :
{ chr(lettre):lettre for lettre in range(65,91) } # Dictionnaire des lettres de l'alphabet en majuscule avec leur valeur ascii

# Set :
{ lettre for lettre in "sharebase" } # Ensemble des lettres contenu dans "sharebase"
```

## Tuples

La syntax est : **(** **valeur ajoutée** `boucle` **condition d'ajout** **)**

Exemples :
```py
( i for i in range(10) ) # Liste immutable de nombres allant de 0 à 9 (inclus)
```

# Aller plus loin, Code Golfing

Depuis le début nous voyons comment *ajouter* des valeurs mais rien ne dit que nous nous intéressons vraiment au contenu de la liste.
En code golfing quand nous devons avoir le code le plus petit possible nous nous intéressons plutôt aux propriétés de taille qu'on les listes par compréhensions.

Un exemple qui illustrera bien :
```py
[print(i) for in range(5)]

""" Affichage :
0
1
2
3
4
"""
```
C'est bien ce que vous pensez. Nous faisons une boucle de print !<br>
Bien sûr la liste sera rempli de *"trucs"* inutilisables mais nous n'avons pas fait ça pour les valeurs et la création d'une liste mais plutôt la possibilité d'effectuer une boucle avec le moins de caractères de code possible.