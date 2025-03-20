---
name: selfhost
---
> [!warning] Avertissement
> Vous devrez potentiellement modifier votre pare-feu et/ou la configuration de votre routeur Internet pour permettre d’accéder à Stend depuis l'extérieur.

## Installation classique ^classic

### Prérequis

- Une version récente de [Node.js]([https://nodejs.org/en/](https://nodejs.org/fr/download/package-manager)) et de [npm](https://www.npmjs.com/) (fournis avec Node.js)
	- Stend a été principalement testé avec Node.js v20
	- Vous pouvez vérifier la version installée avec la commande `node --version`
- [Git CLI](https://git-scm.com/) (optionnel, facilite l’installation et les mises à jour)
- Un serveur permettant de servir des fichiers statiques (la majorité des hébergements WEB, ou un VPS par exemple)

### Installation

```component
<Steps>
	<Step>
		### Télécharger le code source

			#### Avec Git

			```bash
			git clone https://github.com/hoststend/stend-web.git
			```

			#### Sans Git

			Depuis un navigateur, allez sur [le dépôt GitHub de Stend](https://github.com/hoststend/stend-web.git) et cliquez sur le bouton vert "Code" puis sur "Download ZIP".

			Vous pourrez ensuite extraire les fichiers dans un dossier de votre choix. Ouvrez un terminal dedans.
	</Step>

	<Step>
		### Configurer le client

		Ouvrez un terminal dans le dossier de Stend (naviguez avec `cd stend-web`) puis exécutez ces commandes :

		```bash
		mv .env.example .env
		nano .env
		```

		Vous pouvez maintenant modifier les valeurs de votre fichier `.env` pour configurer certains éléments. Pas d'inquiétude, des commentaires seront inclus dans le fichier pour vous aider.
	</Step>

	<Step>
		### Installer et compiler le client

		<Tabs items={["pnpm", "npm", "yarn", "bun"]}>
			```bash tab="pnpm"
			pnpm install
			pnpm build
			```

			```bash tab="npm"
			npm install
			npm run build
			```

			```bash tab="yarn"
			yarn install
			yarn run build
			```

			```bash tab="bun"
			bun install
			npm run build
			```
		</Tabs>
	</Step>

	<Step>
		### Démarrer Stend

		Le client a été compilé et un dossier `build` contenant les fichiers finaux, prêts à être servis, a été créé. Vous pouvez maintenant : configurer un serveur web (comme Apache ou Nginx) pour servir ces fichiers sur un serveur, utiliser un hébergeur statique (comme [Vercel](https://vercel.com/new) ou [GitHub Pages](https://pages.github.com)), ou démarrer le client temporairement sur votre PC avec `npm run start`.
	</Step>
</Steps>
```

## Installation sur Dokploy

Il est possible de configurer rapidement une instance sur [Dokploy](https://dokploy.com) en liant le Dockerfile disponible sur [GitHub](https://github.com/hoststend/stend-api/blob/main/Dockerfile).

```component
<Steps>
	<Step>
		### Créez un service

		Depuis votre dashboard, dans un projet, créez un nouveau service "Application" et donnez lui le nom que vous souhaitez.
	</Step>

	<Step>
		### Configurer le service

		Définissez le provider sur Git :

		- Repository URL: `https://github.com/hoststend/stend-web.git`
		- Branch: `main`
		- Build Path: `/`
		- Watch Paths: *(empty)*

		Définissez également "Build Type" sur "Dockerfile" et utiliser "Dockerfile" comme fichier source.
	</Step>

	<Step>
		### Configurer les réglages

		Des réglages par défaut sont appliqués pour faciliter un déploiement rapide, vous pouvez cependant utiliser les réglages d'environnement pour définir vos propres modifications. La liste des variables est [disponible ici](https://github.com/hoststend/stend-web/blob/main/.env.example).

		Cependant, il est nécessaire de commencer en ajoutant les variables d'environnement suivantes :

		```env
		FILE_MAX_SIZE="x GB"
		API_BASE_URL="https://stend-api.example.com"
		SHOW_HTML_EXTENSION="false"
		```

	</Step>

	<Step>
		### Finalisation

		- Lors de l'ajout d'un domaine, le port à utiliser est `80` si vous n'avez pas apporté de modifications à la variable d'environnement `PORT`.
		- Pensez à faire un nouveau déploiement après avoir modifié les réglages liés à l'environnement ou aux domaines.
		- Il est conseillé d'ajouter la variable d'environnement `FILE_MAX_SIZE` pour permettre d'afficher sur l'accueil la limite maximale d'envoi supportée par l'API.
	</Step>
</Steps>
```

## Installation via Docker ^docker

Il est possible de configurer rapidement le client via une image Docker publiée par [Make In Lab](https://it.makeinlab.fr) (non affiliée avec Stend). Il est recommandé d’écrire un unique `docker-compose.yml` contenant l’[API](/api-docs/selfhost#docker) et le client WEB pour profiter de meilleures performances, cet exemple ne contiendra que les instructions pour le client WEB.

```component
<Steps>
	<Step>
		### Créez un dossier

		```bash
		mkdir stend-web
		cd stend-web
		```
	</Step>

	<Step>
		### Écrire le docker-compose.yml

		Vous aurez maintenant besoin de créez un fichier `docker-compose.yml` dans le dossier actuel. Vous pouvez copier cet exemple de configuration en modifiant les variables d'environnement que vous pensez être importantes.

		```dockercompose
		version: '3'
 
		services:
			stend-web:
				image: makeinlab/stend-web:latest
				environment:
					# Texte affiché sur le site pour indiquer la taille maximale autorisée par fichier
					FILE_MAX_SIZE: 5 GB

					# URL de l'API, doit pouvoir être accédée par le client, une erreur sera affichée dans la console du navigateur dans le cas contraire
					# Une adresse IP locale (localhost, 127.0.0.1, ...) ne fonctionnera pas si l'utilisateur du site n'est pas sur le même réseau que le serveur
					API_BASE_URL: https://stend-demo-api.exemple.com

					# Port sur lequel le serveur web écoutera
					PORT: 80

					# Afficher ".html" dans le chemin des fichiers ?
					# Le serveur intégré dans cette image est capable de servir des fichiers HTML sans l'extension ".html" dans l'URL
					# Exemple - false : https://stend.example.com/d?frezazer (recommandé)
					# Exemple - true : https://stend.example.com/d.html?frezazer
					SHOW_HTML_EXTENSION: false
				ports:
					- 80:80
				volumes:
					- stend_web:/usr/src/app/build

		volumes:
			stend_web:
		```
	</Step>

	<Step>
		### Démarrer le conteneur à l'avant-plan

		Cette étape permet de démarrer le client WEB de Stend dans votre terminal, sans détacher le processus, cela vous permettra de repérer immédiatement des potentielles erreurs, vaut mieux être prudent. Si vous êtes sûr que tout fonctionne, vous pouvez ignorer cette étape et passer à la suivante.

		```bash
		docker compose up
		```

		![Démarrer le conteneur à l'avant-plan](stend_web_dockercomposeup.png)
	</Step>

	<Step>
		### Démarrer le conteneur en arrière-plan

		Une fois sûr que tout fonctionne, arrêter le service avec CTRL+C, et exécuter cette commande pour démarrer le client WEB en tâche de fond. Vous pourrez alors fermer votre terminal.

		```bash
		docker compose up -d
		```
	</Step>

	<Step>
		### Dernière vérification

		Assurez-vous que le client fonctionne en ouvrant un navigateur et en vous rendant sur `http://<local ip>`. Si le serveur tourne sur le même ordinateur, vous pouvez directement ouvrir [`http://localhost`](http://localhost).

		Si vous rencontrez un problème, ouvrez la console de votre navigateur (les réglages Développeur doivent être activés sur Safari) et tentez de lire les erreurs, ou [demander de l'aide](https://github.com/hoststend/stend-web/issues/new).

		|         | Windows / Linux    | macOS              |
		| ------- | ------------------ | ------------------ |
		| Chrome  | `Ctrl + Shift + J` | `Cmd + Option + J` |
		| Firefox | `Ctrl + Shift + K` | `Cmd + Option + K` |
		| Safari  |                    | `Cmd + Option + C` |

> [!tip] Astuce
> Pensez à effacer le cache ou à essayer en navigation privée lorsque vous faites des modifications, le site garde toujours une copie des ressources dans votre navigateur, et les efface lorsque la version dans le fichier `package.json` change.

	</Step>
</Steps>
```
