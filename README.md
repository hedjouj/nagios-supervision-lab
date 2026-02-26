# nagios-supervision-lab

Mise en place d’une supervision avec Nagios Core

Contexte

Dans le cadre d’un TP d’examen, j’ai mis en place une solution complète de supervision avec Nagios Core sur un serveur Linux.

L’objectif était de superviser plusieurs services critiques d’une infrastructure afin de garantir leur disponibilité et leur bon fonctionnement.

Ce travail m’a permis de manipuler la configuration réelle de Nagios, de comprendre son fonctionnement interne et de résoudre plusieurs problèmes techniques liés aux permissions, aux plugins et aux dépendances système.

Environnement

Serveur Linux Debian

Nagios Core 4.4.2

Plugins Monitoring Plugins

Configuration manuelle des fichiers

Interface Web Nagios

Services supervisés
1. Supervision HTTPS du site livecampus.fr

Objectif :
Vérifier que le site web sécurisé est accessible.

Mise en place :

Utilisation du plugin check_curl

Gestion du SSL et du SNI

Vérification du temps de réponse

Vérification de la présence de la chaîne "livecampus"

Résultat :
Le service HTTPS remonte en statut OK avec contrôle du temps de réponse.

Compétences mobilisées :

Diagnostic SSL

Résolution d’erreurs handshake

Adaptation du plugin check_http vers check_curl

2. Supervision du serveur DHCP

Objectif :
Vérifier que le serveur DHCP attribue bien des adresses IP.

Mise en place :

Utilisation du plugin check_dhcp

Identification de l’interface réseau correcte

Gestion des permissions pour autoriser l’utilisation du port 68

Problème rencontré :
Erreur de permission liée aux sockets réseau.

Solution :
Configuration des capacités système pour permettre l’exécution du plugin avec les droits nécessaires.

Résultat :
Le service DHCP_LiveCampus est en statut OK.

Compétences mobilisées :

Analyse des erreurs système

Gestion des permissions Linux

Compréhension du fonctionnement du protocole DHCP

3. Supervision du serveur FTP externe

Objectif :
Vérifier la disponibilité du serveur ftpperso.free.fr.

Mise en place :

Création d’un host dédié

Utilisation du plugin check_ftp

Configuration propre avec séparation host/service

Résultat :
Le service FTP_LiveCampus est en statut OK.

Compétences mobilisées :

Modélisation correcte d’un host externe

Bonne pratique de configuration Nagios

4. Supervision du SWAP du serveur

Objectif :
Surveiller l’utilisation de la mémoire swap du serveur local.

Mise en place :

Création de la commande check_swap

Définition des seuils d’alerte warning et critical

Validation via test manuel avant intégration

Résultat :
Service SWAP_LiveCampus en statut OK.

Compétences mobilisées :

Création personnalisée de commandes Nagios

Vérification des seuils système

5. Supervision de l’espace disque

Objectif :
Éviter la saturation du disque du serveur.

Seuils définis :

Warning si moins de 100 Mo libres

Critical si moins de 50 Mo libres

Mise en place :

Utilisation du plugin check_disk

Surveillance de la partition racine

Résultat :
Service DISK_LiveCampus en statut OK.

Compétences mobilisées :

Paramétrage de seuils adaptés

Surveillance proactive des ressources

Difficultés rencontrées et résolution

Pendant ce projet, plusieurs problèmes techniques ont été rencontrés :

Erreurs SSL avec check_http

Problèmes de permissions avec check_dhcp

Erreurs de configuration bloquant le démarrage de Nagios

Définitions dupliquées dans les fichiers de configuration

Chaque problème a été analysé via :

Vérification des logs

Tests manuels des plugins

Validation avec la commande nagios -v

Corrections directes dans les fichiers de configuration

Cela m’a permis de comprendre que la supervision ne consiste pas seulement à installer un outil, mais à savoir diagnostiquer et corriger des erreurs réelles en environnement système.

Ce que ce projet démontre

Capacité à installer et configurer Nagios Core manuellement

Compréhension du fonctionnement des plugins

Gestion des permissions Linux

Résolution d’erreurs réseau et SSL

Lecture et correction de fichiers de configuration

Méthodologie de test avant mise en production

Conclusion

Ce TP m’a permis de travailler dans des conditions proches d’un environnement réel d’administration systèmes et réseaux.

J’ai appris à :

Mettre en place une supervision complète

Diagnostiquer des erreurs techniques

Structurer proprement une configuration Nagios

Travailler de manière méthodique

Ce projet renforce ma capacité à assurer la disponibilité des services et à intervenir efficacement en cas d’incident.