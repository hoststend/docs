---
name: download
---
**GET** `/files/download`

## Paramètres

Query `?sharekey=...&token=...`

- `sharekey` : clé de partage du transfert
- `token` : token de téléchargement, généré par l'API lors de la lecture des détails d'un fichier

> [!tip] Astuce
> Vous pouvez aussi utiliser le chemin `downloadLink` de la réponse de l'API lorsque vous [lisez les détails d’un transfert](/api-docs/endpoints/reading/details) pour ne pas avoir à définir les paramètres.

## Authentification

Aucune.

## Réponse

Le fichier en question si tout s'est bien passé, ou une erreur dans le cas contraire.
