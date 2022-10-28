---
layout: post
comments: true
title: "Opérateurs binaires"
date: 2022-10-28 09:14:37
image: '/assets/img/'
description: "Dictionnaire des opérateurs binaires"
main-class: "dev"
color:
tags:
- dev
categories:
twitter_text: "Dictionnaire des opérateurs binaires"
introduction: "Dictionnaire des opérateurs binaires"
---

# Introduction

**C'est quoi une opération binaire ?** C'est une opération normal comme une addition, une multiplication mais spécifique aux régles du processeurs. Donc ce ne seront pas les opérateurs arithmétiques +, -, \*, /, \*\*, % mais ***AND et OR*** qui s'appliqueront directement sur les valeurs binaires et non décimal.

**Pourquoi s'embêter à les utiliser ?** De nos jours, loin de l'ère de l'assembleur nous pouvons nous passer de ces opérateurs mais si vous voulez coder parfois plus facilement en C ou souhaitez avoir un code qui s'exécute drastiquement plus rapidement, les opérateurs binaires sont vos amis.

**AND et OR ? Et pour NOT et XOR ?** Très bonne remarque ! Bien sûr nous utiliserons NOT et XOR mais il faut savoir que NOT et XOR peuvent être fait juste avec des AND et OR ! *Enfin plus précisément, TOUT peut être fait à partir de NAND, même AND et OR.*

| A | B | A OR B | A NAND B | (A OR B) AND (A NAND B) | A XOR B |
|:-:|:-:|:------:|:--------:|:-----------------------:|:-------:|
| 0 | 0 |   0    |    1     |           0             |    0    |
| 1 | 0 |   1    |    1     |           1             |    1    |
| 0 | 1 |   1    |    1     |           1             |    1    |
| 1 | 1 |   1    |    0     |           0             |    0    |

| A | 1 | A XOR 1 | NOT A |
|:-:|:-:|:-------:|:-----:|
| 0 | 1 |    1    |   1   |
| 1 | 1 |    0    |   0   |

**On écrit ça comment dans notre code ?** Là on touche à un problème, chaque langage à sa propre version d'écrire ces opérateurs. Par exemple ``^``, pour certains ce sera un XOR et pour d'autres le symbole de l'exponentiation (Autre exemple, Python n'a pas ``&&`` et ``||`` mais directement ``and`` et ``or`` !). Il faut aussi ajouter que certains langages ne supportes pas les opérateurs d'affection, les &=, \|=, ^=, !=, etc... Ce qui rend plus énervant l'écriture 😒

# Table des symboles

Table selon les conventions. Comme expliqué précédemment, regardez la documentation de votre langage ! De plus en électricité les symboles ne sont pas les mêmes, faîtes attention à ne pas donner une crise cardiaque à vos professeurs.

| AND | OR | XOR | NOT | Left bit shift | Right bit shift |
|:---:|:--:|:---:|:---:|:--------------:|:---------------:|
|  &  | \| |  ^  |  !  |      \<\<      |       \>\>      |

**\|\|, \|, &&, &, on s'y perd ! C'est quoi la différence ?** Dans des langages comme C on a ``&&`` et ``||`` qui sont des **opérateurs conditionnelles qui retourne Vrai ou Faux** et qu'on retrouve dans des structures conditionelles comme ``If (A && B)`` ou ``If (A || B)``. Les **opérateurs binaires** sont des opérations comme AND et OR qui **s'effectuent sur CHAQUE bits** et sont représentés par seulement 1 caractère, ``&``, ``|``, etc...

# Dictionnaire des opérateurs

## Opérateurs binaires

### AND

*Retourne Vrai seulement si A et B sont Vrais.*

Utilisé comme **élément basique** pour des opérations plus complexes. Permet d'**effectuer des masques**, prendre seulement une certaine partie d'un nombre binaire. Permet de **remplacer des IF** facilement.

| A | B | A AND B |
|:-:|:-:|:-------:|
| 0 | 0 |    0    |
| 1 | 0 |    0    |
| 0 | 1 |    0    |
| 1 | 1 |    1    |

Exemple de masque :
```c
a      = 0b10011001
masque = 0b00001111 // On sélectionne seulement les 4 derniers bits
c = a & masque

// Valeur de c -> 0b00001001
```

### OR

*Retourne Vrai seulement si A ou B sont Vrais.*

Utilisé comme **élément basique** pour des opérations plus complexes. Très pratique pour **"passer" des bits** d'opérations en opérations.

| A | B | A OR B |
|---|---|--------|
| 0 | 0 |   0    |
| 1 | 0 |   1    |
| 0 | 1 |   1    |
| 1 | 1 |   1    |

### XOR

*Aussi appelé "OU exclusif". Retourne Vrai seulement si A ou B sont Vrais et A et B ne sont pas Vrais tout les deux.*

Possède la **proprité de "retomber sur ses pas"** comme un Rubik's cube, l'opération peut sembler impréssionnante mais si on la répète encore et encore on retourne sur notre valeur binaire de départ (le temps pour cycler dépend de l'opération et du nombre de bits avec lequel on travail). Opération excellente dans certains problèmes **pouvant faciliter le calcul *drastiquement***. Utilisé en **Cryptologie** de façon extensive.

| A | B | A XOR B |
|---|---|---------|
| 0 | 0 |    0    |
| 1 | 0 |    1    |
| 0 | 1 |    1    |
| 1 | 1 |    0    |

### NOT

*Retourne l'inverse, si A est Faux alors NOT A retourne Vrai et inversement*

Opérateur TRES utile dans beaucoup d'opérations. Utilisé notamment pour faire **"apparaître" des Vrais** ce qui est nécessaire dans la majorité des opération.

| A | NOT A |
|---|-------|
| 0 |   1   |
| 1 |   0   |

## Opérateurs de décalage de bits

Dans la plupart des opérations complexes il est nécessaire de décaler les bits. En AND et OR cela devient plus que fastidieux. C'est pour ça que nous avons les **opérateurs de décalage de bits** qui permettent de décaler de X bits vers la droite ou la gauche votre valeur binaire.

Ces opérations sembles un peu abstraites mais elle peuvent facilement relier au "monde réel" si on affiche leur valeur décimal. Par exemple si je décale de 2 vers la gauche j'obtiens mon nombre fois 2 ! Et vers la droite ? On divise notre nombre par 2 ! **Quand on décale de X bits on fait une multiplication/division par $$2^{x}$$**.

### Left Bit Shift

*Décale de X bits vers la gauche et fait apparaître un 0 à droite*

Exemple :
```c
a = 0b1111
b = a << 1
c = a << 3

// Valeur de b -> 0b1110
// Valeur de c -> 0b1000
```

### Right Bit Shift

*Décale de X bits vers la gauche et fait apparaître un 0 à droite*

Exemple :
```c
a = 0b1111
b = a >> 1
c = a >> 3

// Valeur de b -> 0b0111
// Valeur de c -> 0b0001
```