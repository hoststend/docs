---
name: commands
---
Pour faciliter la gestion et l’utilisation du client Terminal de Stend, les fonctionnalités principales et celles liées à la configuration sont séparées en deux commandes `stend` et `stend-config`.

## `stend` (alias : `std`)

Sans argument, la commande affichera un menu pour utiliser la plupart des sous-commandes via une interface en ligne de commande.

### `help` / `h`

Affiche une page d’aide, avec la liste des sous-commandes et options disponibles.

### `version` / `v`

Affiche la version du CLI.

### `configpath` / `cp`

Indique le chemin du fichier de configuration du client.

### `download` / `d`

Télécharge un ou plusieurs fichiers à partir d’une instance Stend. Le premier argument doit être un lien vers la page de téléchargement du fichier via le client web, ou la clé de partage si le fichier est partagé sur l’instance configurée. Il est possible d’utiliser l’option `--dest` pour définir le chemin de destination du fichier téléchargé.

### `upload` / `u`

Envoie un ou plusieurs fichiers vers l’instance Stend configurée. Chaque argument doit être le chemin vers un fichier, il n’est pas possible d’envoyer un dossier. Il est possible d’utiliser l’option `--expire` pour définir la durée en minutes avant que le transfert n’expire.

### `info` / `i`

Affiche des informations sur un transfert à l’aide de sa clé de partage ou du lien de la page de téléchargement.

### `history`

Met en forme une liste des derniers transferts envoyés depuis le CLI.

### `follow-instructions` / `fi`

Créé un nouveau transfert basé sur des instructions définies dans un fichier. Le chemin du fichier d’instructions doit être le premier argument (après la sous-commande.) Une page dédiée à cette fonctionnalité est [disponible ici](/cli-docs/instructions).

## `stend-config`

Sans argument, la commande supprimera les valeurs d’authentification enregistrées, et vous demandera de les renseigner à nouveau via une interface en ligne de commande.

### `get <clé>`

Affiche dans le terminal la valeur d’un élément de la configuration, à partir d’une clé.

### `set <clé> <valeur>`

Définit une valeur dans la configuration à partir d’une clé.

### `delete <clé>`

Supprime une valeur de la configuration à partir de sa clé.

### `list`

Affiche dans le terminal la liste des clés de configuration disponibles.

### `path`

Affiche le chemin vers le fichier de configuration, `stend configpath` permet aussi de la retourner.
