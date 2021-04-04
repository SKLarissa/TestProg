# Test de Programmation pour recrutement sous contrat CIFRE à PaintUP.

Dans ce document, j'explique la démarche que j'ai utilisé pour résoudre le problème, je donne quelques spécifications sur les classes que j'ai crée et j'explique mon application.

## Approche de Resolution du Test
En observant la liste des problème à resoudre, j'ai remarqué que :
- L'on a deux principaux types de problème : les problèmes de type "minimisation de fonction" (P1 et P4) et les problèmes de type "minimisation de distance" (P2 et P4).
- Chacun de ces problèmes présente un "nombre de variable" et les limites inférieures et supérieures de l'espace de recherche.
- Les problèmes P1 et P4 ont un nombre de variable égale à 1. Dons l'espace de recherche est de dimension 1.
- Les problèmes P2 et P3 ont une dimension de l'espace de recherche supérieure à 1. Par défaut, 2.
Seulement, chaque problème est identifié par sa fonction à minimiser.

## Mise en place des classes et des fonctions
Ainsi donc pour résoudre ce problème, j'ai définit trois classes :
- Une classe nommée "ProblemeOptimisation" qui est la classe parent. Les objets de cette classe possède comme attribut le nombre de variable, un tableau contenant les limites inféreieures de chaque dimension et un autre tableau contenant les limites supérieures de chaque dimension.
- Une classe nommée "Probleme14" (pour faire reférence aux problèmes de type minimisation de fonction: P1 et P4). Cette classe a comme attribut le sous type de problème identifié par un entier(La valeur 2 pour le type P4 et tout autre entier pour le type P1). Cet attribut permet de définir la fontion à minimiser.
- Une classe nommée "Probleme23" (pour faire reférence aux problèmes de type minimisation de fonction: P2 et P3).Cette classe a comme attribut le sous type de problème identifié par un entier(Valeur 2 : Minimisation de la distance par rapport à 2 points (P3); Valeur 3: Minimisation de la distance par rapport à 2 points (Pas demandé,Bonus), Minimisation de la distance par rapport à 4 points (P4)). Cet attribut permet de définir la fontion à minimiser.

Les classes "Probleme14" et "Probleme23" dérive de la classe "ProblemeOptimisation".

Les Solveurs S1, S2, S3, S4 et S6 sont définis dans la classe "ProblemeOptimisation" en tant que méthode virtuelle (Concept Polymorphisme).
Ainsi donc, dans chacune des classes dérivées, se trouve une redéfinition des solveurs S1, S2, S3, S4 et S6 car ils dépendent de la fonction à minimiser.

Les Solveurs S5 et S7 quant à eux sont définis une seule fois dans la classe "ProblemeOptimisation".

En plus, j'ai définit deux autres fonctions d'écriture dans le fichier "result.txt"
- La première est la fonction d'écriture du texte d'erreur,
- La seconde est la onction d'écriture des valeurs recherchées dans le fichier.


## Comment executer mon application?
Pour éxecuter mon applicaction sous Ubuntu, procéder ainsi :
A partir du terminal,
- Définir comme repertoire courant le dossier "bin" contenu dans le dossier "build".
- Donner à la variable "LD_LIBRARY_PATH" le chemin d'access de la bibliothèque "libOptimisation-d.so" contenu dans le dossier "lib". Par exemple si le chemin d'access de la bibliothèque "libOptimisation-d.so" sur mon PC est:"/home/larissa/Bureau/TestProg/b uild/lib" alors je dois saisir la commande : "LD_LIBRARY_PATH=/home/larissa/Bureau/TestProg/b uild/lib" et appuyer sur la touche "Entrer.
- saisir la commande :  "export LD_LIBRARY_PATH" et appuyer sur la touche "Entrer.
- saisir ensuite la commande : "./Optim", appuyer sur la touche "Entrer"
A ce moment, mon application demarerra en affichant sur le terminal le message suivant: "Saisir le nom du solveur et le nom du problème respectivement : "
  
Les solveurs sont identifiés par :
S1 : Solveur du milieu
S2 : Discrétisation par 10
S3 : Discrétisation par 10 successif
S4 : Solveur aléatoire
S5 : Solveur aléatoire itératif
S6 : Suivi de chemin
S7 : Suivi de chemin itératif

Les problèmes sont identifiés par :
P1 : Fonction du deuxième ordre à une variable
P2 : Trouver le point P={x, y} e plus proche de deux points P1 et P2 connus;
P3 : Trouver le point P={x, y} le plus proche de quatre points P1,P2,P3 et P4 connus
P4 : fonction exponentielle

Exemple : Si je veux minimiser une "Fonction du deuxième ordre à une variable" par le "solveur du milieu", Je procède ainsi :
- Je saisie "S1"
- J'appuie sur la touche "Entrer"
- Je saisie "P1"
- J'appuie sur la touche "Entrer"


Le resultat sera écrit dans le fichier "result.txt" contenu dans le dossier bin.


