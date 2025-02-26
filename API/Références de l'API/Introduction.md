---
name: intro
---

## URL de base de l'API

Si vous hébergez Stend sur votre propre serveur, vous devrez utiliser l'URL de votre instance pour faire vos requêtes. Par exemple, si vous hébergez Stend sur [`localhost:3000`](http://localhost:3000), la requête vers `/instance` sera à l'URL [`http://localhost:3000/instance`](http://localhost:3000/instance)

## Version

L’API de Stend n’est pas versionnée. Une requête vers [`/instance`](/api-docs/endpoints/instance/details) vous permettra de savoir la version utilisée par celles-ci. Des changements pourraient être apportés à l’API dans le futur.

## Authentification

Chaque page correspondante à une requête dans cette documentation vous indiquera s’il est nécessaire de s’authentifier et par quelle manière. Dans la plupart des cas, il ne sera demandé un mot de passe que si l'instance a été configurée pour en demander un.

## Format de réponses

Toutes les réponses de l’API seront au format JSON. Le format d’une réponse avec succès peut varier.

Les réponses avec erreurs devraient toujours suivre ce format suivant, mais peuvent être différentes selon la configuration du serveur web par l’administrateur de l’instance (ex : reverse proxy qui retourne une erreur) :
```json
{
  "statusCode": 400, // n'est pas toujours identique
  "error": "Titre de l'erreur",
  "message": "Description de l'erreur, peut être affichée à l'utilisateur et devrait rester comphréensible"
}
```

## Rate Limit

Aucune limite de requêtes n’est actuellement imposée, mais cela changera dans le futur.
