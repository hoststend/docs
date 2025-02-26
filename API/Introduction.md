---
name: intro
---
L'API est l'élément central de Stend. Il doit être installé sur un serveur afin de permettre à vous ou à vos proches d'y envoyer et d'y télécharger des fichiers. Celui-ci gère les transferts, la base de données, les accès ainsi que tous les paramètres essentiels.

Pour installer cet élément, vous pouvez [suivre ce guide](/api-docs/selfhost).

## Protéger l’instance par mot de passe

Il est possible d’appliquer un mot de passe à votre instance de Stend, celui-ci permet d’empêcher un malfaiteur d’envoyer des fichiers sur votre serveur sans que vous le souhaitiez, mais laisse la possibilité de télécharger un fichier dont la clé de transfert est connue. **Par défaut, le mot de passe est défini sur `password` !**

> [!warning] Avertissement
> À l’heure actuelle, un maximum d’un seul mot de passe ne peut être défini, et il n’est pas possible de créer des comptes utilisateurs individuels. Cette limite pourrait être modifiée dans une future mise à jour.

Pour définir ou redéfinir le mot de passe d’une instance, connectez-vous (en SSH par exemple) au serveur qui l’héberge, localisez le dossier de stend-api, et ouvrez le fichier [`.env`](https://github.com/hoststend/stend-api/blob/main/.env.example). Ce fichier permet de configurer certaines réglages comme vous le souhaitez, nous aurons besoin de modifier la ligne débutant par `API_PASSWORD=`.

Vous pouvez laisser un vide après le signe égal pour désactiver la protection, ou bien y inscrire le mot de passe que vous souhaitez. N’oubliez pas de sauvegarder le fichier et de redémarrer l’instance après les modifications.

## Gérer une instance en tant qu’administrateur

Aucun tableau de bord ou méthode externe n'a été implémenté pour gérer une instance. Cependant, vous pouvez exécuter un script dédié depuis le terminal, permettant de gérer différents éléments de votre instance, tels que la suppression de transferts.

```component
<Tabs items={["Installation classique", "Installé via Docker"]}>
	```bash tab="Installation classique"
	# Rendez-vous dans le dossier de votre instance
	cd stend-api

	# Gérer l'instance (interactif)
	npm run admin

	# --- OU --- Gérer l'instance (via commandes)
	node admin.js info <clé de partage> # Affiche les informations d'un transfert
	node admin.js delete <clé de partage> # Supprime un transfert, sans demander confirmation
	node admin.js storage # Affiche l'espace de stockage utilisé par les fichiers enregistrés
	```

	```bash tab="Installé via Docker"
	# Obtenir l'identifiant du conteneur
	docker container list

	# Gérer l'instance (interactif)
	docker exec -ti <container id> node admin.js

	# --- OU --- Gérer l'instance (via commandes)
	docker exec -ti <container id> node admin.js info <clé de partage> # Affiche les informations d'un transfert
	docker exec -ti <container id> node admin.js delete <clé de partage> # Supprime un transfert, sans demander confirmation
	docker exec -ti <container id> node admin.js storage # Affiche l'espace de stockage utilisé par les fichiers enregistrés
	```
</Tabs>
```
