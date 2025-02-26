---
name: uploadchunk
---
**PUT** `/files/uploadChunk`

> [!tip] Astuce
> Un chunk est un morceau de fichier, coupé pour éviter d’envoyer une requête trop lourde d’un coup au serveur.

> [!warning] Avertissement
> Chaque chunk doit être envoyé dans l'ordre, en commençant par le premier chunk (position 0).

## Paramètres

Body : chunk contenu dans un `multipart/form-data`

Query : `?transferkey=...&chunk=...`

- `transferkey` : clé de transfert, générée par l'API lors de la création d'un fichier
- `chunk` : position du chunk, commence à 0 puis augmente selon la taille du fichier

> [!tip] Astuce
> Vous pouvez aussi utiliser le chemin `uploadPath` fourni dans l'array `chunks` de la réponse de l'API lorsque vous [créez un fichier](/api-docs/endpoints/creating/createfile) pour ne pas avoir à définir les paramètres.

## Authentification

Aucune.

## Réponse

Aucun contenu (HTTP 200) s'il reste d'autres chunks à envoyer. Sinon, la réponse est un JSON contenant les informations complètes sur le transfert :

```json
{
  "fileName": "nom du fichier", // nom du fichier, ou "Sans nom"
  "fileSize": "taille du fichier en octets", // taille du fichier
  "shareKey": "clé de partage", // clé à utiliser pour partager ou obtenir des informations sur le transfert
  "expireTime": "temps d'expiration en secondes", // durée en secondes avant que le transfert ne soit supprimé
  "created": 1689794692135, // date de création en millisecondes
  "transferKey": "kob60erqard6", // clé de transfert
  "uploaded": true, // true, puisque le fichier a été envoyé dans son intégralité
  "chunkEvery": 20000000, // taille maximale d'un chunk en octets
  "chunks": [ // liste de tous les chunks à envoyer
    {
      "pos": 0, // position du chunk
      "uploaded": true, // true, car le chunk a été envoyé
      "size": 723955, // taille du chunk en octets
    }
  ],
  "uploadedAt": 1689794692136, // date où le fichier a été envoyé dans son intégralité
  "expireDate": 1689794692137, // date d'expiration du transfert
  "deleteKey": "erfsvgd43gdl", // clé de suppression, à utiliser pour supprimer manuellement le transfert
  "fileType": "type de fichier" // type de fichier, en fonction du nom ou de l'extension de celui-ci, n'est pas retourné si impossible à déterminer
}
```
