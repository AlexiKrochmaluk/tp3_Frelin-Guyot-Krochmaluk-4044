# TP 3
## Exercice 1 Commandes de base
1. Quels sont les 5 derniers paquets installés sur votre machine ?
2. Utiliser dpkg et apt pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !).
Comment explique-t-on la (petite) différence de comptage ?
3. Combien de paquets sont disponibles en téléchargement ?
4. Créer un alias ”maj” qui met à jour le système
5. A quoi sert le paquet fortunes ? Installez-le.
6. Quels paquets proposent de jouer au sudoku ?
7. Lister les derniers paquets installés explicitement avec la commande apt install

1. ```console dpkg -l | tail -n 5 ``` pour afficher les 5 derniers packets installés.
2.```console dpkg -l | wc -l ``` nous donne le nombre de paquets installés (505) ```console apt list --installed | wc -l ``` aussi (501). Dpkg, ne gère pas les dépendances, donc affiche plus de paquets que apt qui lui les gère et va donc compacter en un certains paquets.
3.```console apt list | wc -l ``` nous donne le nombre de paquets téléchargeables (62482).
4.```console alias maj="apt-get update" ```crée un alias pour mettre à jour le système.
5.```console apt show fortunes ``` Le paquet fortunes contient 15000 biscuits Chinois. On l'installe avec ```console apt-get install fortunes ```
6.Il existe 8 paquets permettant de jouer au sudoku ```console apt search sudoku ```

7.```console cat /var/log/apt/history.log | grep "install:" ``` Affiche les derniers paquets installés avec apt install.

## Exercice 2

A partir de quel paquet est installée la commande ls ? Comment obtenir cette information en une seule
commande, pour n’importe quel programme (indice : la réponse est dans le poly de cours 2, dans la liste des
commandes utiles) ? Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension
.sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée

```console dpkg -S /bin/ls ``` /bin/ls se trouve dans le package coreutils. 
La commande est which "commande" | xargs dpkg -S (on utilise xargs car dpkg -S ne prend pas l'entrée standard)

```console
#!/bin/bash

command=$1

which $command | xargs dpkg -S
```

## Exercice 3
Ecrire une commande qui affiche ”INSTALLÉ” ou ”NON INSTALLÉ” selon le nom et le statut du package
spécifié dans cette commande.

```console [[ $(dpkg -l mon_paquet | wc -l) -eq 1 ]] && echo "Installé" || echo "Non Installé"```

## Exercice 4
Lister les programmes livrés avec coreutils. A quoi sert la commande ```[``` et comment afficher ce qu’elle
retourne ?

```dpkg -L coreutils``` affiche la liste des programmes

La commande```[``` sert à effectuer des tests sur les valeurs et types de fichier.
On ajoute echo puis les valeurs en cas de conformité du test séparées par un ```||```
ex : ```["ac" = "ab"] && echo "True" || echo "False"``` affichera alors "False"

## Exercice 5
Installez le paquet emacs à l’aide de la version graphique d’aptitude
```
ctrl T pour accéder aux items du menu
/ pour find un fichier
n pour next (une fois dans le find)
+ pour installer un pack
g pour preview install puis g pour lancer install
```

