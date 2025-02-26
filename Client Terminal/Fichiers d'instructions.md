---
name: instructions
---
Si vous souhaitez utiliser le CLI de Stend comme moyen d'automatiser l'envoi d'un ou plusieurs fichiers, vous pouvez utiliser la sous-commande `follow-instructions` de celui-ci, suivie du chemin vers un fichier d'instruction valide. Cette fonctionnalité a été conçue pour faciliter certaines tâches automatisées, sans avoir d’impacts sur l’environnement en cours.

## Explication

Un fichier d'instruction est un fichier texte, sous n’importe quel format, contenant une liste d'instructions à exécuter par le CLI de Stend. Chaque instruction est séparée par un retour à la ligne, les lignes vides sont ignorées.

Exemple :

```bash
# Options d'authentifications, celles de la configuration seront utilisées si elles ne sont pas définies ici
WEB_BASE_URL https://stend-demo.johanstick.fr
API_BASE_URL https://stend-demo-api.johanstick.fr
API_PASSWORD aaaaaaaaa

# Options d'envoi / de comportement, celles par défaut seront utilisées si elles ne sont pas définies ici
EXPIRE_AFTER 5
SILENT_OUTPUT true
DISABLE_NOTIFICATIONS true
DISABLE_SPINNER true
DISABLE_PROMPT false
DISABLE_AUTO_WRITE_CLIPBOARD true
DISABLE_HISTORY false
 
# Liste des fichiers, doit forcément être la dernière instruction, doit être précédée par "--- FILES"
--- FILES
unexemple.txt
unexemple2.txt
```

> [!warning] Avertissement
> Vous ne pouvez pas utiliser de commentaires dans un fichier d'instruction. Les lignes commençant par `#`dans cet exemple ne servent qu'à expliquer le fonctionnement du fichier.

## Erreurs à gérer

Le CLI peut afficher différentes erreurs, la liste est disponible ici :

* `Veuillez entrer le chemin d'un fichier d'instructions valide.`
* `Impossible de suivre ce fichier d'instructions. Le fichier n'a pas pu être lu.`
* `Impossible de suivre ce fichier d'instructions. Chargement des paramètres impossibles - API_BASE_URL manquant.`
* `Impossible de suivre ce fichier d'instructions. Chargement des paramètres impossibles - EXPIRE_AFTER manquant.`
* `Impossible de suivre ce fichier d'instructions. Chargement des paramètres impossibles - FILES manquant.`
* Ainsi que les différentes erreurs pouvant être affichées lors d'un simple envoi.

## Liste d’instructions disponibles

### Authentification

> [!warning] Avertissement
> Si l’URL de l’API n’est pas défini, les trois options seront récupérés depuis la configuration. Si elle n’est pas présente dedans, une erreur sera renvoyée et le transfert ne pourra pas débuter.

* `WEB_BASE_URL` (facultatif) : URL de base du client WEB, sans slash à la fin
* `API_BASE_URL` : URL de base de l'API, sans slash à la fin
* `API_PASSWORD` (facultatif) : Mot de passe de l'API, dans le cas où il est nécessaire d’en fournir un

### Comportement

> [!warning] Avertissement
> Ces options sont facultatives, à l'exception de `EXPIRE_AFTER` qui doit toujours être définie.

* `EXPIRE_AFTER` : Durée de vie des fichiers avant qu’ils n’expirent (en minutes)
* `SILENT_OUTPUT` : Indique au CLI d'afficher moins d'informations, d’icônes, de détails.
* `DISABLE_NOTIFICATIONS` : Empêche des notifications d’apparaître sur le bureau à la fin de l'envoi
* `DISABLE_SPINNER` : Remplace les barres de chargement par des objets JSON
* `DISABLE_PROMPT` : Assure que le CLI ne demandera rien à l'utilisateur
* `DISABLE_AUTO_WRITE_CLIPBOARD` : Désactive l'ajout de l'URL finale dans le presse-papier
* `DISABLE_HISTORY` : Désactive l'ajout de l'URL finale dans l'historique

### Liste de fichiers

Cette instruction doit être la dernière du fichier d'instruction. Les chemins des fichiers sont séparés par un retour à la ligne, et doivent être entrés après la ligne `--- FILES`.
