---
name: intro
---
Ce serveur global permet d'apporter des mini fonctionnalités aux services proposés par Stend. Celui-ci ne va pas remplacer l'API principale ainsi que les clients disponibles, mais va permettre de centraliser certains éléments qui n'auraient jamais pu être implémentés dans un serveur décentralisé.

Le serveur n’est pas directement connecté dans l’API, il est implémenté dans les clients supportés, et vous pouvez jeter un coup d’œil aux services proposés qui justifient cet emploi.

## Compte

Ce service inclut un système de compte, complètement séparé des autres services proposés par Stend, basé sur une authentification avec Google pour faciliter l'intégration dans tous les clients. Il est possible de demander une suppression des données assignées depuis une interface compatible ou en [contactant le support](https://johanstick.fr/contact).

Les endpoints de l'API de ce serveur permettent d'avoir le contrôle complet sur les comptes utilisateurs : connexion et création, réinitialiser les sessions en cours et même le supprimer.

> [!warning] Avertissement
> L’API n’est pas versionné, et les requêtes pour gérer un compte pourraient changer au fil du temps. Il est possible que d’autres fournisseurs que Google arrivent dans le futur.

## Héberger soi-même

Il est inutile d'installer ce service chez soi puisqu'aucun client officiel ne permet d’utiliser une autre instance. Vous pouvez tout de même consulter le code source sur GitHub et proposer des modifications avec une issue ou une pull request.

## Fonctionnalités

```component
<Cards>
	<Card
		href="/global-server/features/expose"
		title="Exposition des transferts"
	/>
</Cards>
```
