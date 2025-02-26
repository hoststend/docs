---
name: intro
---

## URL de base de l'API

[`https://globalstend.johanstick.fr`](https://globalstend.johanstick.fr)

## Version

L’API n’est pas versionnée. Une requête vers [`/instance`](https://globalstend.johanstick.fr/instance) vous permettra de savoir la version utilisée par celles-ci. Des changements pourraient être apportés dans le futur.

## Authentification

Chaque page correspondante à une requête dans cette documentation vous indiquera s’il est nécessaire de s’authentifier, ou alors dans quel cas il l’est.

Si nécessaire, vous aurez besoin d’inclure un header `Authorization` qui contient le token qui vous a été renvoyé au moment où vous avez [finalisé la connexion](/global-server/endpoints/auth/checkcode).

## Format de réponses

Toutes les réponses de l’API seront au format JSON. Le format d’une réponse avec succès peut varier.

Les réponses avec erreurs devraient toujours suivre ce format suivant :
```json
{
  "statusCode": 400, // n'est pas toujours identique
  "error": "Titre de l'erreur",
  "message": "Description de l'erreur, peut être affichée à l'utilisateur de manière comphréensible"
}
```

## Rate Limit

La plupart des endpoints fournis par cette API disposent de limites par IP afin de protéger les données des utilisateurs.

Pour vous aider, chaque réponse contiendra les headers `X-Ratelimit-Limit`, `X-Ratelimit-Remaining` et `X-Ratelimit-Reset` ; ils indiquent le nombre de requêtes maximum autorisées, le nombre de requêtes restantes pour votre adresse IP et le temps avant que le compteur soit remis à zéro.
