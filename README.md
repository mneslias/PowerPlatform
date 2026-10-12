# Gestion de tickets clients — Power Platform

Mini-projet de découverte de **Microsoft Power Apps**, **Power Automate** et **SharePoint** pour centraliser le suivi de tickets clients et automatiser une notification lors de la modification d’un fichier.

> **Projet pédagogique / exploratoire** — cette réalisation a pour objectif de prendre en main les outils Power Platform. Elle peut contenir des choix simplifiés et n’est pas présentée comme une solution prête pour la production.

## Sommaire

- [Description du projet](#description-du-projet)
- [Objectifs de découverte](#objectifs-de-découverte)
- [Technologies utilisées](#technologies-utilisées)
- [Schéma des données](#schéma-des-données)
- [Fonctionnalités clés](#fonctionnalités-clés)
- [Prérequis](#prérequis)
- [Exécuter le projet](#exécuter-le-projet)
- [Captures d’écran](#captures-décran)
- [Améliorations possibles](#améliorations-possibles)
- [Fichiers fournis](#fichiers-fournis)
- [Licence](#licence)

## Description du projet

L’objectif est de construire un parcours simple de gestion des demandes clients :

1. les informations d’un ticket sont stockées dans SharePoint ;
2. une application Power Apps permet de consulter et de manipuler ces informations ;
3. un flux Power Automate réagit à la modification d’un fichier et envoie un e-mail ;
4. le rapport Power BI fourni peut servir de support d’exploration et de restitution des données.

La solution s’appuie sur un jeu de données de tickets comprenant les informations client, le produit concerné, le canal de contact, le statut du traitement et les indicateurs de délai ou de satisfaction.

## Objectifs de découverte

- Découvrir la création d’une application métier avec Power Apps.
- Comprendre le raccordement d’une application à une source SharePoint.
- Mettre en place un premier scénario d’automatisation avec Power Automate.
- Explorer la structuration d’un jeu de données destiné au suivi de tickets.
- Identifier les possibilités de restitution et d’analyse avec Power BI.
- Observer les limites d’un prototype et les améliorations nécessaires avant un usage réel.

## Technologies utilisées

| Technologie | Rôle dans le projet |
| --- | --- |
| **Power Apps** | Interface de consultation et de gestion des tickets clients. |
| **SharePoint** | Stockage et organisation des données de tickets. |
| **Power Automate** | Déclenchement d’une action à la modification d’un fichier, puis envoi d’un e-mail. |
| **Power BI** | Exploration et visualisation des données de tickets. |

## Schéma des données

Les données brutes incluses dans ce dépôt. Le schéma ci-dessous décrit les colonnes principales utilisées par le projet.

| Colonne | Description |
| --- | --- |
| `Ticket ID` | Identifiant unique du ticket. |
| `Customer Name` | Nom du client. |
| `Customer Email` | Adresse e-mail du client. |
| `Customer Age` | Âge du client. |
| `Customer Gender` | Genre renseigné pour le client. |
| `Product Purchased` | Produit acheté ou concerné par la demande. |
| `Date of Purchase` | Date d’achat du produit. |
| `Ticket Type` | Type ou catégorie de la demande. |
| `Ticket Subject` | Objet synthétique du ticket. |
| `Ticket Description` | Description détaillée de la demande. |
| `Ticket Status` | État d’avancement du ticket. |
| `Resolution` | Résolution apportée, lorsqu’elle est disponible. |
| `Ticket Priority` | Niveau de priorité attribué au ticket. |
| `Ticket Channel` | Canal utilisé pour contacter le support. |
| `First Response Time` | Délai avant la première réponse. |
| `Time to Resolution` | Durée nécessaire à la résolution. |
| `Customer Satisfaction Rating` | Évaluation de satisfaction laissée par le client. |

> **Données personnelles :** dans un contexte réel, les informations client doivent être protégées, minimisées et traitées conformément aux règles de sécurité et de confidentialité applicables. Les données présentées ici sont décrites sans être reproduites dans le dépôt.

## Fonctionnalités clés

- Consultation des informations essentielles d’un ticket.
- Suivi du statut, de la priorité et de la résolution.
- Recherche ou filtrage possible selon les champs disponibles dans l’application.
- Centralisation des informations clients et support dans une source SharePoint.
- Notification automatique par e-mail lorsqu’un fichier est modifié.
- Première exploration des délais de réponse, délais de résolution et niveaux de satisfaction.

### Flux Power Automate

Le flux documenté dans ce projet suit le scénario suivant :

<img width="208" height="143" alt="image" src="https://github.com/user-attachments/assets/64f81d40-db86-4691-bbc6-40dd03d72498" />
<img width="688" height="335" alt="Capture d&#39;écran 2026-10-12 103826" src="https://github.com/user-attachments/assets/9042e6cc-9c5b-4cdd-a0b3-015f9bd0599e" />


La capture de détail indique un **temps économisé simulé de 50 minutes** sur les sept derniers jours, selon l’hypothèse de 10 minutes économisées par exécution réussie et 5 exécutions. Il s’agit d’une estimation illustrative, et non d’une mesure de productivité réelle.

## Améliorations possibles

- Ajouter une gestion robuste des erreurs et des notifications en cas d’échec du flux.
- Prévoir des règles de validation des champs et des transitions de statut.
- Définir des rôles distincts pour les agents, responsables et lecteurs.
- Ajouter une journalisation des changements et un historique des actions.
- Améliorer la recherche, le tri, la pagination et l’accessibilité de l’application.
- Remplacer les données personnelles par des identifiants ou des vues restreintes lorsque cela est possible.
- Sécuriser les connexions, les environnements et les variables de configuration.
- Documenter les dépendances et automatiser le déploiement entre environnements.
- Mesurer le gain réel du flux sur une période représentative plutôt que d’utiliser uniquement l’estimation simulée.

## Fichiers fournis

| Fichier | Description |
| --- | --- |
| `Application tickets.msapp` | Application Power Apps du projet. |
| `Tickets.pbix` | Rapport Power BI associé au suivi des tickets. |
| `assets/power-automate-flow.png` | Capture du flux Power Automate. |
| `assets/power-automate-details.png` | Capture des détails du flux et de l’estimation de temps économisé. |
