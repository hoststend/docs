---
name: checkcode
---
**GET** `/auth/checkcode`

## Paramètres

Query `?code=...`

- `code` : un code d'accès temporaire généré pour votre compte, reçu après une [connexion via Google](/global-server/endpoints/auth/google-login).

## Authentification

Aucune.

## Réponse

```json
{
  "success": true,
  "token": "...",
  "action": "SAVE_TOKEN"
}
```
