---
name: createfile
---
**POST** `/files/create`

> [!tip] Astuce
> Pour envoyer un fichier à une instance Stend, vous aurez besoin de créer un transfert (cette requête) puis d’y [envoyer tous les chunks](/api-docs/endpoints/creating/uploadchunk) demandés. Si vous souhaitez envoyer plusieurs fichiers, vous aurez besoin de créer plusieurs transferts et de les [regrouper](/api-docs/endpoints/creating/merge).

## Paramètres

```json
{
  "filename": "nom du fichier", // facultatif, sera "Sans nom" si non défini, limité à 200 caractères
  "filesize": "taille du fichier en octets", // obligatoire, limité à la taille maximale de l'instance
  "sharekey": "clé de partage", // facultatif, limité à 30 caractères, sans caractères spéciaux, en minuscules (ignoré si déjà utilisé par un autre transfert)
  "expiretime": "temps d'expiration en secondes", // obligatoire, doit être inférieur à la limite définie par l'instance
}
```

## Authentification

Si l'instance est protégée par un mot de passe, un header `Authorization` doit être présent et doit le contenir. Il sera ignoré si l'instance n'est pas protégée.

## Réponse

```json
{
  "fileName": "nom du fichier", // celui que vous avez envoyée, ou "Sans nom"
  "fileSize": "taille du fichier en octets", // taille que vous avez envoyée
  "shareKey": "clé de partage", // clé générée aléatoirement, ou celle que vous avez envoyée
  "expireTime": "temps d'expiration en secondes", // durée avant expiration que vous avez envoyé
  "created": 1689794692135, // date de création en millisecondes
  "transferKey": "kob60erqard6", // clé de transfert, à utiliser pour envoyer les chunks
  "uploaded": false, // false, puisque le fichier n'a pas encore été envoyé dans son intégralité
  "chunkEvery": 20000000, // taille maximale d'un chunk en octets
  "chunks": [ // liste de tous les chunks à envoyer
    {
      "pos": 0, // position du chunk
      "uploaded": false, // false, car le chunk n'a pas encore été envoyé
      "size": 723955, // taille du chunk en octets, doit être respecté
      "uploadPath": "/files/uploadChunk?transferkey=kob60erqard6&chunk=0" // chemin de l'API à utiliser pour envoyer le chunk
    }
  ]
}
```
