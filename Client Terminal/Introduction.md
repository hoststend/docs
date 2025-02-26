---
name: intro
---
Le client pour terminal vous permet de partager des fichiers (envoyer et recevoir) directement depuis la ligne de commande. Cela peut être utile pour automatiser ou faciliter certaines tâches sur certains environnements. Il supporte les fonctionnalités essentielles de l'API et est compatible avec les principaux systèmes d'exploitation.

![Configurer et envoyer depuis le CLI de Stend](stend_cli_configupload.png)

## Installation

```component
<Steps>
	<Step>
		### Installer NodeJS

		Vérifier si [NodeJS](https://nodejs.org/fr/) est déjà installée en exécutant `node --version` dans un terminal. Si une erreur est affichée, ou que la version retournée est inférieure à 20, vous devrez (ré)installer avec la commande suivante :

		<Tabs items={["macOS", "Windows", "Linux (Debian)"]}>
			```bash tab="macOS"
			brew install node
			```

			```bash tab="Windows"
			winget install OpenJS.NodeJS
			```

			```bash tab="Linux (Debian)"
			curl -fsSL https://deb.nodesource.com/setup_21.x | sudo -E bash - &&\
			sudo apt-get install -y nodejs
			# Note: sous cette distribution, la version de NodeJS installée par défaut est très ancienne. Le script ci-dessus permet d'installer une version plus récente.
			```
		</Tabs>
	</Step>

	<Step>
		### Installer le CLI de Stend

		Exécutez simplement la commande suivante dans votre terminal :

		```bash
		npm install --global stend-cli
		```
	</Step>

	<Step>
		### Configurer le CLI

		Une fois installé, vous devrez configurer certains paramètres du client avant de pouvoir l'utiliser. Pour cela, exécutez la commande suivante :

		```bash
		stend-config
		```
	</Step>
</Steps>
```
