---
name: reset
---
**POST** `/account/reset`

## Paramètres

Aucun.

## Authentification

Nécessite un token valide, défini avec le header `Authorization`.

## Réponse

```json
{
  "success": true,
  "token": "...",
  "action": "SAVE_TOKEN"
}
```
