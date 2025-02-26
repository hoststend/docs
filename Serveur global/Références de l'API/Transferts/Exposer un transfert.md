---
name: create
---
**POST** `/transferts/create`

## Paramètres

```json
{
  "fileName": "file.txt",
  "webUrl": "https://stend.example.com/d.html?aaaaaa",
  "expiresTime": 60, // (en minutes, défini sur 60 si non défini ou si supérieur à 60)
  "nickname": "Johan",
 
  "apiUrl": "https://stend-api.example.com", // --> méthode d'exposition "IP + Instance"
  "latitude": 48.866667, // --> méthode d'exposition "À proximité"
  "longitude": 2.333333, // --> méthode d'exposition "À proximité"
}
```

> [!warning] Avertissement
> Au moins une méthode d'exposition doit être activée. La liste des méthodes activées sera disponible dans la réponse finale.

## Authentification

Facultatif, permet d'activer la méthode d'exposition "Compte".

## Réponse

```json
{
  "success": true,
  "transferId": "O6e8g4nYiTyawmzM",
  "nickname": "Johan",
  "fileName": "file.txt",
  "method": {
    "instanceAndIp": true,
    "location": true, // À proximité
    "account": false
  }
}
```
