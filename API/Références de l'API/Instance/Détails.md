---
name: details
---
**GET** `/instance`

## Paramètres

Aucun.

## Authentification

Aucune.

## Réponse

```json
{
  "fileMaxSize": 60000000000, // taille maximale d'un fichier en octets
  "chunkSize": 20000000, // taille d'un chunk en octets
  "requirePassword": true, // si l'instance requiert un mot de passe pour créer un transfert
  "apiVersion": "1.0.0", // version de l'API
  "fileMaxAge": "2592000", // durée de vie maximale d'un fichier en secondes
  "maxTransfersInMerge": 50, // nombre maximum de transferts dans un groupe de transferts (50 depuis la v2.0, 10 sur les versions plus anciennes)
  "recommendedExpireTimes": [ // durées avant expiration qui pourraient être proposées à l'utilisateur (varient automatiquement en fonction de "fileMaxAge")
    {
      "label": "30 minutes",
      "inSeconds": 1800,
      "value": 30
    },
    {
      "label": "6 heures",
      "inSeconds": 21600,
      "value": 360
    },
    {
      "label": "12 heures",
      "inSeconds": 43200,
      "value": 720
    },
    {
      "label": "1 jour",
      "inSeconds": 86400,
      "value": 1440
    },
    {
      "label": "4 jours",
      "inSeconds": 345600,
      "value": 5760
    },
    {
      "label": "1 semaine",
      "inSeconds": 604800,
      "value": 10080
    },
    {
      "label": "2 semaines",
      "inSeconds": 1209600,
      "value": 20160
    },
    {
      "label": "1 mois",
      "inSeconds": 2592000,
      "value": 43200
    }
  ]
}
```
