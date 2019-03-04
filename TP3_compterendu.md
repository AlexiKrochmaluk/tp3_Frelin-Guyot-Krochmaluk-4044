# TP 2
## Variables d'environnement

Dossier BASH : /.bashrc
- LANG : codage et langue du système
- PWD : chemin courant
- OLDPWD : ancien chemin courant
- SHELL : chemin du shell
- _ : chemin de la commande printenv

SET MY_VAR existe dans le contexte de la première console, mais pas dans la deuxième car c'est une variable LOCALE.
En transformant MY_VAR en variable d'environnement, elle devient disponible dans toutes les instances de console car elle est stockée dans les variables d'environnement.

On crée la variable d'environnement NOMS avec export NOMS="Maxime Antonin", l'espace est bien géré.

Affichons les avec la commande : echo "Bonjour à vous, "$NOMS

Unset : la variable n'existe plus, valeur vide, la variable existe mais a une valeur vide.

Afficher le chemin : echo '$HOME = '$HOME
