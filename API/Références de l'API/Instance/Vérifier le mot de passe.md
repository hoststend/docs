---
name: checkpassword
---
**POST** `/checkPassword`

## Paramètres

Aucun.

## Authentification

Un header `Authorization` doit être présent avec le mot de passe à vérifier comme valeur.

## Réponse

Une erreur indiquant que le mot de passe n’est pas correct / n’est pas nécessaire, ou un message de succès :

```json
{
  "success": true
}
```
