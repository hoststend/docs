---
name: features
---
Pour améliorer votre expérience lors du transfert de fichiers, Stend pour Mobile propose différentes fonctionnalités uniques pour vous aider.

## Envoi de fichiers ^send-files

* À partir des fichiers locaux, de la galerie ou de la caméra
* Envoi de plusieurs fichiers à la fois (transferts groupés)
* Choix de la durée avant expiration, et de la clé de partage
* Possibilité de raccourcir le lien final du transfert
* Partage avec la fiche système, et copie dans le presse-papier
* Indication de la progression pendant l'envoi
* Possibilité d’[exposer un transfert](/global-server/features/expose)

## Téléchargement de fichiers ^download-files

* Téléchargement rapide via un QR code ou le presse-papier
* Téléchargement de plusieurs fichiers en même temps depuis un transfert groupé
* Accéder aux fichiers récemment envoyés avec possibilité de les re-télécharger, partager, ou supprimer
* Supporte les liens raccourcis menant à une instance WEB de Stend, et détecte les réglages de l’API utilisée par celui-ci
* Supporte certains services tiers
* Détecte les URLs présentes dans un texte

## Réglages ^settings

* Configuration rapide d’une instance
* Vérification des mises à jour disponibles pour l'app
* Options (d’autres sont disponibles) :
	* Enregistrer les médias dans la galerie au lieu des téléchargements
	* Copier l'URL dans le presse-papier après la création d’un transfert
	* Télécharger les fichiers dans un sous-dossier (sur Android)
	* Définir la page qui s’ouvre au démarrage
	* Définir le thème utilisé (clair, sombre, selon le système)
	* Activer ou désactiver certaines [méthodes d’exposition](/global-server/features/expose)
	* Possibilité de désactiver l’historique, de choisir le service utilisé pour les URLs raccourcis, de choisir la caméra utilisé pour scanner un QR Code
* Utilise les couleurs Material You sur Android, réglables dans les réglages sur iOS
* Gestion du compte sur le [serveur global](/global-server/intro) (effacer les sessions actives, supprimer le compte, …)
* Vérifier l'état des services principaux connectés (API et client WEB configuré, Serveur Global, …)

## Services pour le téléchargement

| Service                                   | Problème de compatibilité                                                                                       |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Stend via l’API définit dans les réglages | Entièrement supporté                                                                                            |
| Stend via l’URL d’un client WEB           | Entièrement supporté                                                                                            |
| WeTransfer                                | Ne supporte pas les transferts protégés par mot de passe ; les dossiers peuvent parfois présenter des problèmes |
| Free Transfer                             | Ne supporte pas les transferts protégés par mot de passe                                                        |
| Swisstransfer                             | Ne supporte pas les transferts protégés par mot de passe                                                        |
| Smash                                     | Ne supporte pas les transferts protégés par mot de passe                                                        |
| Mediafire                                 | Ne supporte pas les dossiers ; certains fichiers manque leur extension                                          |
