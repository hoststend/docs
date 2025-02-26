---
name: details
---
**GET** `/files/info`

## Paramètres

Query `?sharekey=...`

- `sharekey` : clé de partage du transfert

## Authentification

Aucune.

## Réponse

**Groupe de transferts :**

```json
{
  "uploaded": true, // toujours true
  "transferKey": null, // toujours null
  "deleteKey": null, // toujours null, un groupe de transferts se supprime quand tous les sous transferts sont supprimés
  "fileName": null, // toujours null
  "isGroup": true, // indique que c'est un groupe de transferts
  "groups": [ // liste des clés de partage de chaque transfert
    "uneclé",
    "uneautre",
    "encoreuneautre"
  ]
}
```

**Transfert simple :**

```json
{
  "fileName": "nom du fichier", // nom du fichier
  "fileSize": 50276, // taille du fichier en octets
  "expireTime": 600, // temps en secondes avant que le fichier n'expire, en partant de la date de création
  "created": 1689860988156, // date de création en millisecondes
  "uploaded": true, // true, puisque le fichier a été envoyé dans son intégralité
  "uploadedAt": 1689860988221, // date d'upload du fichier
  "expireDate": 1689861588221, // date d'expiration du fichier
  "fileType": "type de fichier", // type de fichier, en fonction du nom ou de l'extension de celui-ci, n'est pas retourné si impossible à déterminer
  "downloadLink": "/files/download?sharekey=clédepartage&token=tokendetéléchargement" // chemin à utiliser pour télécharger le fichier, le token expire au bout de 2 heures
}
```
