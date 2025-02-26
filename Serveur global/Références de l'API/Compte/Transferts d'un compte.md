---
name: transferts
---
**GET** `/account/transferts`

## Paramètres

Aucun.

## Authentification

Nécessite un token valide, défini avec le header `Authorization`.

## Réponse

```json
{
  "success": true,
  "userId": "google/1234567890",
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
  ]
}
```
