---
name: options
---
Diverses options sont disponibles dans le CLI de Stend, elles peuvent être utilisées pour modifier temporairement le comportement de l'utilitaire.

## Deux types d’options

### Options dans la commande

Une option dans la commande, parfois appelée "flag", est un argument qui commence par un (`-`) ou deux tirets (`--`) et qui modifie le comportement de la commande.

Une valeur peut leur être associée en l’entrant juste après l’option, séparée par un espace. Exemple : `stend download --option valeur`. Les types "booleans" n’ont pas besoin de valeur.

### Variables d’environnements

Une variable d’environnement est une variable (avec une clé et une valeur) définie dans l’environnement d’exécution d’un processus.

Contrairement aux options dans la commande, les variables d’environnement sont définies en dehors de la commande et sont donc globales à toutes les commandes pour la session en cours.

|                      | Commande                   | Exemple                             |
| -------------------- | -------------------------- | ----------------------------------- |
| macOS / Linux        | `VARIABLE=valeur`          | `STEND_DISABLE_SPINNERS=true`       |
| Windows (PowerShell) | `$env:VARIABLE = "valeur"` | `$env:STEND_ON_CONFLICT = "ignore"` |

## Liste des options

### Mode silencieux

Réduit le nombre de messages, d’icônes et de détails affichés dans la console. Certaines commandes pourraient retourner un objet JSON au lieu d’un texte, à ne pas confondre avec la désactivation des barres de chargement. Rend la réalisation de scripts automatisés plus simple à gérer.

> Valeur par défaut : `false`  
> Type : `boolean`  
> Variable d'environnement : `STEND_SILENT_OUTPUT`  
> Option dans la commande : `--silent` / `-s`

### Désactiver les notifications

Désactive l’envoi de notifications sur le bureau lors de l’envoi ou du téléchargement d’un transfert.

> Valeur par défaut : `false`  
> Type : `boolean`  
> Variable d'environnement : `STEND_DISABLE_NOTIFICATIONS`  
> Option dans la commande : `--disable-notifications`

### Expiration par défaut

Définit le temps nécessaire pour qu'un transfert arrive à expiration. Le temps est en minutes et ne doit pas dépasser la limite imposée par le serveur.

> Valeur par défaut : demande à l'utilisateur  
> Type : `number`  
> Variable d'environnement : `STEND_DEFAULT_EXPIRE`  
> Option dans la commande : `--expire` / `-e`

### Désactiver les barres de chargement

Empêche le CLI d’afficher une barre de progression dans la console. La plupart seront remplacés par des objets JSON qui contiennent les informations de la barre de chargement. Facilite la gestion de scripts automatisés.

> Valeur par défaut : `false`  
> Type : `boolean`  
> Variable d'environnement : `STEND_DISABLE_SPINNERS`  
> Option dans la commande : `--disable-spinners`

### Action par défaut en cas de conflit

Définit l’action à effectuer par défaut lorsqu’un fichier ou un dossier existe déjà dans le dossier de destination pendant le téléchargement d’un transfert. `replace` remplacera le fichier existant par le nouveau, `ignore` ignorera le fichier existant et ne le téléchargera pas, `rename` vous proposera de renommer le fichier si les prompts sont activés.

> Valeur par défaut : demande à l'utilisateur  
> Type : `replace`, `ignore`, `rename`  
> Variable d'environnement : `STEND_ON_CONFLICT`

### Désactiver les prompts

Empêche le CLI de demander des informations à l’utilisateur. Certaines actions peuvent ne pas être effectuées si les prompts sont désactivés et qu’une option par défaut n’est pas définie.

> Valeur par défaut `false`  
> Type : `boolean`  
> Valeur d’environnement : `STEND_DISABLE_PROMPT`

### Désactiver le presse-papier

Empêche le CLI d’écrire dans le presse-papier.

> Valeur par défaut : `false`  
> Type : `boolean`  
> Variable d’environnement : `STEND_DISABLE_AUTO_WRITE_CLIPBOARD`

### Désactiver l’historique

Empêche le CLI d’ajouter des entrées dans l’historique lors de l’envoi d’un fichier.

> Valeur par défaut : `false`  
> Type : `boolean`  
> Variable d’environnement : `STEND_DISABLE_HISTORY`
