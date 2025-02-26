---
name: list
---
**POST** `/transferts/list`

## Paramètres

```json
{
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
  "transferts": [
    {
      "id": "O6e8g4nYiTyawmzM",
      "webUrl": "https://stend.example.com/d.html?aaaaaa",
      "expiresDate": "1721942798013",
      "creationDate": "1721942198013",
      "nickname": "Johan",
      "fileName": "file.txt",
      "methodUsed": "position" // --> méthode d'exposition utilisée pour déterminer ce transfert : account, position (À proximité), instanceAndIp
    }
  ],
  "method": {
    "instanceAndIp": true,
    "location": true, // À proximité
    "account": false
  }
}
```
