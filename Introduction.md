---
name: index
icon: Album
---
Stend est sûrement l'un des meilleurs moyens pour configurer son propre service de partage de fichiers. Ce service a été conçu pour être aussi complet que la plupart des services propriétaires, mais avec une facilité d'installation et de configuration incomparable aux autres projets open-source.

> [!tip]
> Si vous souhaitez tester le service avant de l'installer sur votre propre serveur. Vous pouvez vous connecter à une instance de démonstration limitée.
> Client WEB : https://stend-demo.johanstick.fr ― API : https://stend-demo-api.johanstick.fr


![Accueil du client WEB de Stend](stend_web_homedemo.png)

## Pourquoi utiliser Stend ?

Stend se veut être un service de partage de fichiers rapide et simple, en ayant tout de même des fonctionnalités intéressantes. Voici les principaux avantages en déployant votre instance :

- **Contrôle total :** en hébergeant le service sur votre propre serveur, vous avez un contrôle total sur vos fichiers, et vous pouvez les supprimer à tout moment.
- **Confidentialité :** vos données restent sur votre infrastructure. Aucune donnée n'est envoyée à des tiers, aucun service de suivis n'est utilisé, aucune publicité n'est affichée.
- **Sécurité :** vous pouvez configurer l'utilisation ou non d'un mot de passe, afin de protéger votre instance des personnes malveillantes. Il ne dérangera pas ceux à qui vous envoyer le lien de votre transfert, le téléchargement de fichiers ne demande qu’un clic !
- **Gratuité :** Stend est un projet open-source et gratuit. Vous pouvez l'utiliser sans aucune restriction, et même le modifier si vous le souhaitez.
- **Facilité d'installation :** conçu pour être facilement déployable, vous serez prêt à l’utiliser en seulement quelques minutes.
- **API ouverte :** Stend propose une API ouverte, documentée et simple d'utilisation. Vous pouvez l'utiliser pour automatiser l'envoi ou le téléchargement de fichiers, ou même pour développer votre propre client tiers (on vous en reparle plus bas).

## Pourquoi Stend est né ?

Stend est né d'un constat assez simple : au moment du développement, il n’existait aucun service open-source et auto-hébergeable qui proposait une expérience utilisateur aussi satisfaisante et ouverte, sans réduire la facilité d’installation et d’administration. Les solutions propriétaires étant parfois trop chères ou pas assez complètes, il manquait quelqu’un à l’appel.

Stend a donc été créé afin de régler plusieurs problèmes :
- Remplacer les solutions propriétaires (Wetransfer, Swisstransfer, ...).
- Devenir une alternative viable aux solutions open-source déjà existantes (Firefox Send, ...).
- Ne pas être dépendant de services tiers, qui pourrait même être payant.
- Proposer une limite de taille de fichier plus élevée, en fonction de la configuration de votre serveur :

| Service        | Taille maximale                |
| -------------- | ------------------------------ |
| Stend          | Définissez vos propres limites |
| Swisstransfer  | 50 Go                          |
| Free Transfert | 10 Go si non-abonné            |
| Wetransfer     | 2 Go                           |
| Smash          | 2 Go                           |

## Débuter avec Stend ^get-started

```component
<Steps>
	<Step>
		### Héberger l'API

		Vous devrez commencer par héberger l'API de Stend sur votre propre serveur. Celui-ci va devoir gérer et stocker les fichiers envoyés par les utilisateurs, alors assurez-vous d'avoir un serveur avec un stockage persistant, rapide et suffisant pour vos besoins.

		Vous pouvez lire [ce guide](/api-docs/selfhost) pour obtenir des instructions étape par étape.
	</Step>

	<Step>
		### Héberger le client WEB (recommandé)

		Le client WEB est une interface utilisateur connectée à l'API que vous hébergez pour permettre d'envoyer et de télécharger des fichiers de manière plus propre. Il est recommandé de l'installer puisque c'est le seul moyen d'obtenir un lien de partage pour vos fichiers.

		Vous pouvez lire [ce guide](/web-docs/selfhost) pour obtenir des instructions étape par étape.
	</Step>

	<Step>
		### Utiliser Stend !

		Vous avez fini de configurer Stend sur votre propre serveur. Désormais, vous pouvez utiliser n'importe quel client disponible afin de profiter de toutes les fonctionnalités de votre propre service de partage de fichiers.
	</Step>
</Steps>
```

## Clients disponibles

Un client est un moyen d'accéder aux fonctionnalités de Stend via l'API. Vous pouvez développer votre propre client tiers via la documentation de l'API, ou utiliser un des clients officiels actuellement disponibles

```component
<Cards>
	<Card
		href="/web-docs/intro"
		title="Site WEB"
	/>

	<Card
		href="/mobile-docs/intro"
		title="Appli Mobile"
	/>

	<Card
		href="/cli-docs/intro"
		title="Terminal"
	/>
</Cards>
```

> [!tip] Proposer un client tiers
> Si vous souhaitez que votre client tiers soit ajouté à cette liste, n'hésitez pas à [me contacter](https://johanstick.fr/contact).

## Disclaimer sur l'utilisation de Stend

L'utilisation du service pour des activités illégales n'est pas soutenue par le créateur et celui-ci ne peut être tenu responsable des problèmes matériels, logiciels ou légaux liés à ces utilisations non prévues. Utilisez à vos propres risques et prenez les précautions nécessaires, comme l'ajout d'un mot de passe obligatoire pour envoyer un fichier sur la plateforme.

## Code source

Le code source de l’ensemble des dépôts officiels de Stend sont disponibles sur GitHub et sont sous la licence MIT :

* [Serveur API](https://github.com/hoststend/stend-api)
* [Serveur global](https://github.com/hoststend/stend-globalserver)
* [Client WEB](https://github.com/hoststend/stend-web)
* [Client terminal](https://github.com/hoststend/stend-cli)
* [Client mobile](https://github.com/hoststend/stend-mobile)
