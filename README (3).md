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

Les données brutes ne sont pas incluses dans ce dépôt. Le schéma ci-dessous décrit les colonnes principales utilisées par le projet.

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

```text
Quand un fichier est modifié
            ↓
Envoyer un e-mail (V2)
```

La capture de détail indique un **temps économisé simulé de 50 minutes** sur les sept derniers jours, selon l’hypothèse de 10 minutes économisées par exécution réussie et 5 exécutions. Il s’agit d’une estimation illustrative, et non d’une mesure de productivité réelle.

## Prérequis

- Un compte Microsoft disposant des droits nécessaires sur Power Apps, Power Automate, SharePoint et, si besoin, Power BI.
- Un environnement Power Platform dans lequel importer ou recréer les ressources.
- Une liste ou une source SharePoint configurée avec les colonnes du schéma ci-dessus.
- Les droits de lecture/écriture sur la liste SharePoint et les droits d’envoi d’e-mails pour le connecteur utilisé.
- Le fichier d’application `Application tickets.msapp`.
- Le rapport `Tickets.pbix`, avec ses connexions et autorisations configurées dans l’environnement cible.

## Exécuter le projet

### 1. Préparer SharePoint

1. Créer ou sélectionner un site SharePoint de test.
2. Créer une liste de tickets.
3. Ajouter les colonnes nécessaires en respectant le schéma documenté ci-dessus.
4. Vérifier les types de colonnes : texte, nombre, date, choix et notation selon le besoin.
5. Ajouter uniquement des données de test ou anonymisées.

### 2. Importer l’application Power Apps

1. Ouvrir [Power Apps](https://make.powerapps.com/).
2. Sélectionner l’environnement de travail approprié.
3. Importer le fichier `Application tickets.msapp` ou ouvrir l’application depuis son emplacement partagé.
4. Remplacer, si nécessaire, la connexion SharePoint par celle de l’environnement cible.
5. Vérifier la correspondance entre les noms de colonnes de la liste et ceux utilisés dans l’application.
6. Tester l’affichage, la consultation et la modification d’un ticket avec un compte de test.

> Le lien direct vers l’application n’est pas reproduit dans ce README : il doit être ajouté dans cette section selon les droits d’accès de l’environnement, par exemple : `[Ouvrir l’application Power Apps](URL_DE_L_APPLICATION)`.

### 3. Configurer le flux Power Automate

1. Ouvrir [Power Automate](https://make.powerautomate.com/).
2. Créer ou importer un flux automatisé.
3. Configurer le déclencheur **Quand un fichier est modifié** sur l’emplacement SharePoint ou OneDrive concerné.
4. Ajouter l’action **Envoyer un e-mail (V2)**.
5. Renseigner les destinataires, l’objet et le contenu du message avec les champs dynamiques utiles.
6. Enregistrer le flux, puis effectuer une modification de test.
7. Contrôler l’historique d’exécution et la réception du message.

### 4. Ouvrir le rapport Power BI

1. Ouvrir Power BI Desktop ou le service Power BI selon le format de diffusion souhaité.
2. Charger `Tickets.pbix`.
3. Actualiser les connexions après avoir vérifié la source de données.
4. Contrôler les visuels et les filtres avec un jeu de données de test.
5. Publier uniquement dans un espace autorisé, après validation des règles d’accès aux données.

## Captures d’écran

### Vue du flux

Cette capture présente le déclencheur de modification de fichier et l’action d’envoi d’e-mail.

![Flux Power Automate : modification d’un fichier puis envoi d’un e-mail](assets/power-automate-flow.png)

### Détail et estimation du temps économisé

Cette vue présente les détails du flux et l’estimation simulée de 50 minutes économisées.

![Détails du flux Power Automate et temps économisé simulé](assets/power-automate-details.png)

## Améliorations possibles

- Ajouter une gestion robuste des erreurs et des notifications en cas d’échec du flux.
- Prévoir des règles de validation des champs et des transitions de statut.
- Définir des rôles distincts pour les agents, responsables et lecteurs.
- Ajouter une journalisation des changements et un historique des actions.
- Améliorer la recherche, le tri, la pagination et l’accessibilité de l’application.
- Remplacer les données personnelles par des identifiants ou des vues restreintes lorsque cela est possible.
- Sécuriser les connexions, les environnements et les variables de configuration.
- Ajouter des tests fonctionnels et des scénarios de non-régression.
- Documenter les dépendances et automatiser le déploiement entre environnements.
- Compléter le rapport Power BI avec des indicateurs validés : volume par statut, délai médian de résolution, respect des priorités et satisfaction moyenne.
- Mesurer le gain réel du flux sur une période représentative plutôt que d’utiliser uniquement l’estimation simulée.

## Fichiers fournis

| Fichier | Description |
| --- | --- |
| `Application tickets.msapp` | Application Power Apps du projet. |
| `Tickets.pbix` | Rapport Power BI associé au suivi des tickets. |
| `assets/power-automate-flow.png` | Capture du flux Power Automate. |
| `assets/power-automate-details.png` | Capture des détails du flux et de l’estimation de temps économisé. |

## Licence

Ce projet est proposé sous licence **MIT**, sauf indication contraire dans les fichiers ou le contexte de diffusion.

```text
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

> Le titulaire des droits et l’année peuvent être précisés dans un fichier `LICENSE` séparé avant publication.
