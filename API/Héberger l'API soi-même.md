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
- Une machine avec l'un des trois principaux systèmes d'exploitations
	- Les droits d'administrateur sont requis sous Windows
	- Un stockage persistant est requis (les fichiers ne doivent pas disparaitre au redémarrage)
	- Un stockage et un débit internet rapide est recommandé

```component
<Steps>
	<Step>
		### Télécharger le code source

			#### Avec Git

			```bash
			git clone https://github.com/hoststend/stend-api.git
			```

			#### Sans Git

			Depuis un navigateur, allez sur [le dépôt GitHub de Stend](https://github.com/hoststend/stend-api) et cliquez sur le bouton vert "Code" puis sur "Download ZIP".

			Vous pourrez ensuite extraire les fichiers dans un dossier de votre choix. Ouvrez un terminal dedans.
	</Step>

	<Step>
		### Installer les dépendances

		Ouvrez un terminal dans le dossier de Stend (naviguez avec `cd stend-api`) puis installer les dépendances avec la commande suivante :

		<Tabs items={["pnpm", "npm", "yarn", "bun"]}>
			```bash tab="pnpm"
			pnpm install
			```

			```bash tab="npm"
			npm install
			```

			```bash tab="yarn"
			yarn install
			```

			```bash tab="bun"
			bun install
			```
		</Tabs>
	</Step>

	<Step>
		### Configurer Stend

		```bash
		mv .env.example .env
		nano .env
		```

		Vous pouvez maintenant modifier les valeurs de votre fichier `.env` pour configurer certains éléments de Stend. Pas d'inquiétude, des commentaires seront inclus dans le fichier pour vous aider.
	</Step>

	<Step>
		### Démarrer Stend

		<Tabs items={["pnpm", "npm", "yarn"]}>
			```bash tab="pnpm"
			pnpm start
			```

			```bash tab="npm"
			npm start
			```

			```bash tab="yarn"
			yarn start
			```
		</Tabs>

> [!warning] Avertissement
> Pour que Stend reste actif en arrière-plan, même si vous fermez la session de terminal, vous pouvez installer et utiliser PM2 : `npm install pm2 -g` et `pm2 start index.js --name stend-api`

	</Step>

	<Step>
		### Vérifier l'instance

		Pour vous assurer que l'API est en cours d'exécution, vous pouvez ouvrir un navigateur et vous rendre sur `http://<local ip>:3000/instance`. Si l'API tourne sur le même ordinateur, vous pouvez directement ouvrir [`http://localhost:3000/instance`](http://localhost:3000/instance).

		![Requête pour vérifier l'instance](stend_api_getinstance.png)
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

		- Repository URL: `https://github.com/hoststend/stend-api.git`
		- Branch: `main`
		- Build Path: `/`
		- Watch Paths: *(empty)*

		Définissez également "Build Type" sur "Dockerfile" et utiliser "Dockerfile" comme fichier source.
	</Step>

	<Step>
		### Préserver les fichiers

		Par défaut, les fichiers ainsi que la base de données seront effacés à chaque redémarrage. Pour corriger cela, rendez-vous dans les réglages avancés de votre service et ajoutez un nouveau volume :

		- Mount Type: Volume Mount
		- Volume Name: `stend_storage`
		- Mount Path: `/usr/src/app/storage`
	</Step>

	<Step>
		### Configurer les réglages

		Des réglages par défaut sont appliqués pour faciliter un déploiement rapide, vous pouvez cependant utiliser les réglages d'environnement pour définir vos propres modifications. La liste des variables est [disponible ici](https://github.com/hoststend/stend-api/blob/main/.env.example).

> [!warning] Avertissement
> Il est recommandé de ne pas modifier le chemin utilisé pour le stockage des fichiers (`STORAGE_PATH`) sans revérifier la configuration des volumes.

	</Step>

	<Step>
		### Finalisation

		- Lors de l'ajout d'un domaine, le port à utiliser est `3000` si vous n'avez pas apporté de modifications à la variable d'environnement `PORT`.
		- Pensez à faire un nouveau déploiement après avoir modifié les réglages liés aux volumes, à l'environnement ou aux domaines.
		- Pour accéder à l'interface d'administration, depuis General, cliquez sur "Open Terminal" et exécutez `npm run admin`
	</Step>
</Steps>
```

## Installation via Docker Compose ^docker

Il est possible de configurer rapidement une instance via une image Docker publiée par [Make In Lab](https://it.makeinlab.fr) (non affiliée avec Stend). Il est recommandé d’écrire un unique `docker-compose.yml` contenant le [Client WEB](/web-docs/selfhost#docker) et l’API pour profiter de meilleures performances, cet exemple ne contiendra que les instructions pour l’API.

```component
<Steps>
	<Step>
		### Créez un dossier

		```bash
		mkdir stend-api
		cd stend-api
		```
	</Step>

	<Step>
		### Écrire le docker-compose.yml

		Vous aurez maintenant besoin de créez un fichier `docker-compose.yml` dans le dossier actuel. Vous pouvez copier cet exemple de configuration en modifiant les variables d'environnement que vous pensez être importantes.

		```dockercompose
		version: '3'

		services:
			stend-api:
				image: makeinlab/stend-api:latest
				environment:
					# Taille maximale autorisée par fichier en octets (par défaut: 1000000000 / 1 Go)
					FILE_MAX_SIZE: 1000000000

					# Mot de passe requis avant d'envoyer un fichier
					# Si l'option est vide, aucune information ne sera demandé aux utilisateurs et l'instance ne sera pas protégé
					# Le téléchargement d'un fichier ne demandera jamais ce mot de passe, même si l'option est définie
					API_PASSWORD: password

					# Durée maximale avant qu'un fichier n'expire et ne soit supprimé définitivement (par défaut: 2592000 / 30 jours)
					# Durées recommendées :
					# 1800 = 30 minutes
					# 21600 = 6 heures
					# 43200 = 12 heures
					# 86400 = 1 jour
					# 345600 = 4 jours
					# 604800 = 1 semaine
					# 1209600 = 2 semaine
					# 2592000 = 1 mois
					# 7776000 = 3 mois
					# 15552000 = 6 mois
					# 0 = Ne jamais expirer
					FILE_MAX_AGE: 2592000

					# Port sur lequel l'API écoutera
					PORT: 3000

					# Le serveur est-il derrière un reverse proxy ?
					# Cette valeur est importante, puisqu'une personne malveillante pourrait abuser d'une mauvaise configuration afin de se faire passer pour une autre personne
					# Si "true", l'API utilisera l'header X-Forwarded-For pour récupérer l'adresse IP du client
					# Si "cloudflare", l'API utilisera l'header CF-Connecting-IP pour récupérer l'adresse IP du client
					# Si "false", l'API utilisera l'adresse IP du dernier client contacté
					USING_REVERSE_PROXY: true

					# Taille d'un chunk en octets (par défaut: 20000000 / 20 Mo)
					# Note: assurez-vous que votre configuration (nginx, apache, ...) autorise les requêtes de cette taille
					# Dans le cas contraire, une erreur 413 (Payload Too Large) sera retournée lors de requêtes d'un chunk complet à l'API
					# https://stackoverflow.com/a/37916740/16155654
					CHUNK_SIZE: 20000000

					# Marge lors de la vérification de l'espace disponible sur le disque en octets (par défaut: 100000000 / 100 Mo)
					# Si l'espace sur le disque est inférieur à la taille du fichier + cette marge, l'API refusera de stocker le fichier
					# Sur un environnement où le disque est réservé à Stend, il est recommandé de définir une valeur assez basse (ex: 1000000 / 1 Mo)
					DISK_SPACE_MARGIN: 100000000

					# Chemin où seront stockés les fichiers dans le conteneur (doit être accessible en écriture, contiendra les données utilisateurs)
					# Si ce volume est supprimé, toutes les données utilisateurs seront perdues
					# Dans le cas où cette variable est modifiée, il est nécessaire de modifier le volume correspondant
					STORAGE_PATH: /usr/src/app/stend_storage
				ports:
					- 3000:3000
				volumes:
					- stend_storage:/usr/src/app/stend_storage

		volumes:
			stend_storage:
		```
	</Step>

	<Step>
		### Démarrer le conteneur à l'avant-plan

		Cette étape permet de démarrer l'API de Stend dans votre terminal, sans détacher le processus, cela vous permettra de repérer immédiatement les erreurs que vous auriez pu glisser quelque part. Si vous êtes sûr que votre configuration fonctionne, vous pouvez ignorer cette étape et passer à la suivante.

		```bash
		docker compose up
		```

		![Démarrer le conteneur à l'avant-plan](stend_api_dockercomposeup.png)
	</Step>

	<Step>
		### Démarrer le conteneur en arrière-plan

		Une fois sûr que tout fonctionne, arrêter le service avec CTRL+C, et exécuter cette commande pour démarrer l'API en tâche de fond. Vous pourrez alors fermer votre terminal.

		```bash
		docker compose up -d
		```
	</Step>

	<Step>
		### Vérifier l'instance

		Pour vous assurer que l'API est en cours d'exécution, vous pouvez ouvrir un navigateur et vous rendre sur `http://<local ip>:3000/instance`. Si l'API tourne sur le même ordinateur, vous pouvez directement ouvrir [`http://localhost:3000/instance`](http://localhost:3000/instance).

		![Requête pour vérifier l'instance](stend_api_getinstance.png)
	</Step>
</Steps>
```
