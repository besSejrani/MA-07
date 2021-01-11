# H1
# H1 Se déplacer dans le répertoire de notre utilisateur :
--
* Cd => Change directory
* Cd ~
* Cd/

# H1 Créer un fichier vide :
--
* Touch vide_test1.txt
* Touch vide_ test2.txt
* Touch vide_ test3.txt

# H1 Créer un répertoire :
# (Lors de la création du fichier, le chemin, s'il n'existe pas, est également créé.)
--
Mkdir Test/files/vides4
Rm -R ./ Test

# H1 Créer un fichier ainsi que le chemin manquant :
--
Mkdir -pv ./ Test / files / vides4 && touch vides4

# H1 Chemin absolu vs chemin relatif
--
* Chemin absolu depuis racine
* Chemin relatif depuis un dossier

# H1 More
# H1 (A quoi sert cette commande ? Faire un exemple.)
--
Affiche le contenu d'un fichier ou d'une commande
More loremIpsum.txt

# H1 Comment afficher l'arborescence sous forme d'arbre
Tree chemin du dossier

