---
layout: default
title: Modules
parent: SYD Builder
nav_order: 2
has_children: true
permalink: /builder/modules/
---

# Modules
{: .fs-8 }

Création et configuration des visualisations
{: .fs-5 .fw-300 }

---

## Présentation

Les **modules** sont les briques de base de vos tableaux de bord. Chaque module représente une visualisation de données : graphique, tableau, indicateur, carte, etc.

Un module est composé de :
- **Source de données** : requête SQL 
- **Type de visualisation** : graphique, tableau, indicateur...
- **Configuration d'affichage** : couleurs, légendes, options...
- **Options avancées** : datalabels, export Excel, rafraîchissement...

---

## Types de modules

### Graphiques

| Type | Description | Cas d'usage |
|:-----|:------------|:------------|
| ![Line](https://img.shields.io/badge/-Line-blue) | Courbes | Évolutions temporelles, tendances |
| ![Bar](https://img.shields.io/badge/-Bar-green) | Barres verticales | Comparaisons entre catégories |
| ![HorizontalBar](https://img.shields.io/badge/-HBar-green) | Barres horizontales | Classements, comparaisons |
| ![Pie](https://img.shields.io/badge/-Pie-orange) | Camembert | Répartitions, proportions |
| ![Doughnut](https://img.shields.io/badge/-Doughnut-orange) | Anneau | Répartitions avec valeur centrale |

### Données

| Type | Description | Cas d'usage |
|:-----|:------------|:------------|
| ![Table](https://img.shields.io/badge/-Table-gray) | Tableau | Données détaillées, listes |

### Indicateurs

| Type | Description | Cas d'usage |
|:-----|:------------|:------------|
| ![Indicator](https://img.shields.io/badge/-Indicator-purple) | Chiffre clé | KPIs, métriques principales |
| ![Gauge](https://img.shields.io/badge/-Gauge-red) | Jauge | Progression vers objectif |
| ![Progress](https://img.shields.io/badge/-Progress-teal) | Barre de progression | Avancement, pourcentage |

### Spéciaux

| Type | Description | Cas d'usage |
|:-----|:------------|:------------|
| ![Map](https://img.shields.io/badge/-Map-darkgreen) | Carte géographique | Données géolocalisées |
| ![Iframe](https://img.shields.io/badge/-Iframe-darkblue) | Contenu externe | Pages web, widgets |

---

## Créer un module

### Étape 1 : Accéder à la liste des modules

Dans le menu de navigation, cliquez sur **Modules** pour voir la liste des modules existants.

### Étape 2 : Nouveau module

Cliquez sur le bouton **Nouveau** (ou **+**) pour ouvrir le formulaire de création.

### Étape 3 : Configuration

Le formulaire de module est organisé en onglets :

| Onglet | Contenu |
|:-------|:--------|
| **General** | Titre, sous-titre, type de module, rafraîchissement |
| **Datasource** | Source de données (uniquement à la création) |
| **Affichage** | Options visuelles selon le type de module |
| **Utilities** | Options supplémentaires |
| **Requests** | Gestion des requêtes associées (modules BDD) |
| **Datalabels** | Configuration des étiquettes de données |
| **Excel** | Options d'export Excel |
| **Infos** | Informations sur le module (édition uniquement) |

---

## Configuration générale

<!-- ![Formulaire module - General]({{ site.baseurl }}/assets/img/builder/module-general.png) -->

| Champ | Description |
|:------|:------------|
| **Titre du module** | Titre affiché en haut du module |
| **Sous-titre** | Texte secondaire sous le titre |
| **Type de module** | Type de visualisation |
| **Refresh (ms)** | Intervalle de rafraîchissement automatique (0 = désactivé) |
| **Barre de recherche** | Afficher une barre de recherche (certains types) |
| **Bouton refresh** | Afficher un bouton de rafraîchissement manuel |

---

## Datasource

À la création du module, vous devez choisir la source de données :

- **BDD** : Sélectionnez une requête SQL existante ou créez-en une nouvelle

{: .important }
> Le type de datasource ne peut pas être modifié après la création du module.

---

## Workflows

### Créer un graphique simple

1. Créer une requête SQL retournant les données souhaitées
2. Créer un module, sélectionner le type (Line, Bar, Pie...)
3. Associer la requête au module
4. Configurer les options d'affichage
5. Ajouter le module à un dashboard

### Créer un indicateur

1. Créer une requête retournant une valeur unique
2. Créer un module de type **Indicator**
3. Configurer le format d'affichage (préfixe, suffixe, couleur...)
4. Ajouter le module à un dashboard

---



## Dupliquer un module

La duplication permet de créer rapidement un nouveau module basé sur un module existant, en conservant toute sa configuration (type, requêtes, options d'affichage, etc.).

### Comment dupliquer un module

1. Dans la liste des modules, repérez le module à dupliquer
2. Cliquez sur le bouton **Dupliquer** (icône <i class="fas fa-clone"></i>) dans la colonne d'actions
3. Dans la fenêtre qui s'ouvre, saisissez le **nom du nouveau module**
4. Cliquez sur **Valider**

{: .note }
> Le module dupliqué est une copie indépendante : toute modification sur le nouveau module n'affecte pas l'original et inversement.

### Cas d'utilisation

- Créer des variantes d'un même graphique avec des filtres différents
- Adapter un module existant pour un autre dashboard
- Tester des modifications sans impacter le module original

---

## Prévisualiser un module

La prévisualisation permet de visualiser le rendu d'un module directement depuis la liste des modules, sans avoir à l'intégrer à un dashboard.

### Comment prévisualiser

1. Dans la liste des modules, repérez le module à prévisualiser
2. Cliquez sur le bouton **Prévisualiser** (icône <i class="fas fa-eye"></i>) dans la colonne "Prévisualisation"
3. Le module s'ouvre dans un nouvel onglet avec son rendu final

{: .note }
> La prévisualisation s'exécute dans l'environnement du Visualizer, vous voyez donc exactement ce que verront les utilisateurs finaux.

### Informations affichées

La liste des modules affiche également le **statut d'utilisation** de chaque module :
- ![in use](https://img.shields.io/badge/-in%20use-success) : Le module est utilisé dans au moins un dashboard
- ![not in use](https://img.shields.io/badge/-not%20in%20use-danger) : Le module n'est utilisé dans aucun dashboard

---

## Filtres de recherche

Lorsque le nombre de modules devient important, les filtres de recherche permettent de retrouver rapidement un module spécifique.

### Accéder aux filtres

1. Dans la liste des modules, cliquez sur le bouton **Filtres de recherche**
2. Le panneau de filtres se déplie

### Filtres disponibles

| Filtre | Description |
|:-------|:------------|
| **Créateur du module** | Filtrer par nom de l'utilisateur ayant créé le module |
| **Label du connecteur** | Filtrer par le label de la source de données (base de données) |

### Utilisation

- Les filtres s'appliquent **en temps réel** lors de la saisie
- Les filtres peuvent être combinés pour affiner la recherche
- Cliquez sur **Réinitialiser les filtres** pour effacer tous les critères

{: .note }
> Les filtres sont cumulatifs : si vous saisissez un créateur ET un label de connecteur, seuls les modules correspondant aux deux critères seront affichés.
