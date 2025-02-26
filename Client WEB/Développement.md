---
name: dev
---
Vous pouvez démarrer le serveur WEB de Stend en mode développement, des fonctionnalités supplémentaires pour faciliter le développement seront alors activés (live reload, build de Tailwind CSS en temps réel, etc).

Pour contribuer, vous pouvez suivre les étapes d’[hébergement classique](/web-docs/selfhost#classic), mais exécuter la commande "dev" au lieu de "build" :

```component
<Tabs items={["pnpm", "npm"]}>
	```bash tab="pnpm"
	git clone https://github.com/hoststend/stend-web.git
	
	cd stend-web
	mv .env.example .env
	nano .env
	
	pnpm install
	pnpm dev
	```
	
	```bash tab="npm"
	git clone https://github.com/hoststend/stend-web.git
	
	cd stend-web
	mv .env.example .env
	nano .env
	
	npm install
	npm dev
	```
</Tabs>
```

> [!info]
> Ce client a été conçu avec le framework roc, vous pouvez en apprendre plus depuis son [dépôt GitHub](https://github.com/johan-perso/roc-framework).
