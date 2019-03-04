# TP 3
## Commandes de base

```console dpkg -l | tail -n 5 ``` pour afficher les 5 derniers packets installés.
```console dpkg -l | wc -l ``` nous donne le nombre de paquets installés (505) ```console apt list --installed | wc -l ``` aussi (501). Dpkg, ne gère pas les dépendances, donc affiche plus de paquets que apt qui lui les gère et va donc compacter en un certains paquets.
```console apt list | wc -l ``` nous donne le nombre de paquets téléchargeables (62482).
```console alias maj="apt-get update" ```crée un alias pour mettre à jour le système.
```console apt show fortunes ``` Le paquet fortunes contient 15000 biscuits Chinois. On l'installe avec ```console apt-get install fortunes ```
Il existe 8 paquets permettant de jouer au sudoku ```console apt search sudoku ```

```console cat /var/log/apt/history.log | grep "install:" ``` Affiche les derniers paquets installés avec apt install.

## Exercice 2

```console dpkg -S /bin/ls ``` /bin/ls se trouve dans le package coreutils. 
La commande est

```console
#!/bin/bash

command=$1

which $command | xargs dpkg -S
```

## Exercice 3

```console [[ $(dpkg -l mon_paquet | wc -l) -eq 1 ]] && echo "Installé" || echo "Non Installé"```

## Exercice 4

## Exercice 5
