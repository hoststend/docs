---
name: merge
---
**POST** `/files/merge`

## Paramètres

```json
{
  "sharekey": "clé de partage", // facultatif, clé de partage du groupe de transfert
  "sharekeys": "uneclé,uneautre,encoreuneautre" // liste des clés de partage des transferts à fusionner, séparées par une virgule, sans espace
}
```

## Authentification

Si l'instance est protégée par un mot de passe, un header `Authorization` doit être présent et doit le contenir. Il sera ignoré si l'instance n'est pas protégée.

## Réponse

```json
{
  "shareKey": "rtjklnna", // clé de partage du nouveau groupe de transfert
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
