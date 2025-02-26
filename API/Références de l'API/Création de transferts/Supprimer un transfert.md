---
name: delete
---
**DELETE** `/files/delete`

## Paramètres

Query : `?sharekey=...&deletekey=...`

- `sharekey` : clé de partage du transfert
- `deletekey` : clé de suppression du transfert, renvoyé par l’API lors de l'envoi du dernier chunk

## Authentification

**v2.1.0+ :** Aucune.  
**Avant :** Si l'instance est protégée par un mot de passe, un header `Authorization` doit être présent et doit le contenir. Il sera ignoré si l'instance n'est pas protégée.

## Réponse

```json
{
  "success": true
}
```
