---
name: google-login
---
**GET** `/auth/google/login`

## Paramètres

Query `?responseType=...`

- `responseType` : `plain` (par défaut), `redirect`, `html`

## Authentification

Aucune.

## Réponse

Vous serez redirigé vers la page de connexion via Google. Après authentification, un code d'accès temporaire sera renvoyé à l'utilisateur selon le type de réponse (`responseType`) choisi.

Ce code pourra être échangé contre un token d'accès permanent via l'endpoint [`/auth/checkcode`](/global-server/endpoints/auth/checkcode).

### `responseType=plain`

Texte brut : `1234abcd`

### `responseType=redirect`

Redirection vers [`stend://globalserver/auth?code=1234abcd`](/mobile-docs/protocol)

### `responseType=html`

Une page web contenant le code et des explications pour l’utilisateur.
