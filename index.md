---
layout: default
title: Accueil
nav_order: 1
description: "SYD - Start Your Dashboard : Solution de création et visualisation de tableaux de bord"
permalink: /
---

# SYD - Start Your Dashboard
{: .fs-9 }

Solution complète de création et de visualisation de tableaux de bord interactifs.
{: .fs-6 .fw-300 }

[Commencer avec le Builder](#syd-builder){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Découvrir le Visualizer](#syd-visualizer){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Présentation

**SYD (Start Your Dashboard)** est une solution logicielle développée par [CFD Innovation](https://cfd-innovation.fr/syd-start-your-dashboard/) permettant de créer des tableaux de bord dynamiques et interactifs à partir de différentes sources de données.

Le produit se compose de deux parties distinctes :

### 🛠️ SYD Builder
{: .text-purple-300 }

Interface de conception destinée aux **informaticiens et développeurs** pour :
- Configurer les connecteurs de bases de données 
- Créer et configurer des modules de visualisation (graphiques, tableaux, indicateurs, cartes...)
- Assembler les tableaux de bord
- Gérer les utilisateurs et leurs droits d'accès
- Configurer les formulaires de filtrage

[Accéder à la documentation Builder]({{ site.baseurl }}/builder/){: .btn .btn-outline }

### 📊 SYD Visualizer
{: .text-blue-300 }

Interface de consultation destinée aux **utilisateurs finaux** pour :
- Consulter les tableaux de bord auxquels ils ont accès
- Interagir avec les modules (filtres, drill-down)
- Exporter les données au format Excel
- Naviguer entre les différents dashboards

[Accéder à la documentation Visualizer]({{ site.baseurl }}/visualizer/){: .btn .btn-outline }

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        SYD Builder                          │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────┐│
│  │ Connecteurs │ │   Modules   │ │      Dashboards         ││
│  │  - BDD      │ │  - Charts   │ │  - Layout               ││
│  │  - Requêtes │ │  - Tables   │ │  - Utilisateurs         ││
│  │             │ │  - Maps     │ │  - Catégories           ││
│  └─────────────┘ └─────────────┘ └─────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                      Base de données SYD                    │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                      SYD Visualizer                         │
│  ┌─────────────────────────────────────────────────────────┐│
│  │  Affichage des dashboards pour les utilisateurs finaux  ││
│  └─────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```

---

## Types de modules disponibles

| Type | Description | Idéal pour |
|:-----|:------------|:-----------|
| **Line** | Graphique en courbes | Évolutions temporelles |
| **Bar** | Graphique en barres verticales | Comparaisons |
| **Horizontal Bar** | Graphique en barres horizontales | Classements |
| **Pie** | Graphique en camembert | Répartitions |
| **Doughnut** | Graphique en anneau | Répartitions avec valeur centrale |
| **Table** | Tableau de données | Données détaillées |
| **Indicator** | Indicateur chiffré | KPIs |
| **Gauge** | Jauge | Progression vers un objectif |
| **Progress** | Barre de progression | Avancement |
| **Map** | Carte géographique | Données géolocalisées |
| **Iframe** | Contenu externe | Intégration de pages web |

---

## Captures d'écran

{: .note }

[//]: # (> Les captures d'écran seront ajoutées progressivement dans le dossier `assets/img/`.)

<!-- Placeholder pour les futures captures -->
 ![Mire de connexion]({{ site.baseurl }}/assets/builder/Capture_mire_de_connexion.jpg) 
 ![Liste des modules dans le Builder]({{ site.baseurl }}/assets/builder/Dashboard_demo_liste_des_modules.png) 
 ![Dashboard Visualizer]({{ site.baseurl }}/assets/visualizer/Dashboard_demo_dark_mode_1.png) 

---

## Prérequis techniques

- **Serveur hôte** : IBM i (V7R2+), Linux ou Windows
- **Serveur web** : Apache avec PHP 7.4+
- **Base de données** : DB2 for i ou MySQL 5.7+ / MariaDB
- **Navigateur** : Chrome, Firefox, Edge (versions récentes)

---

## Liens utiles

- [Site officiel CFD Innovation](https://cfd-innovation.fr/)
- [Présentation du produit](https://cfd-innovation.fr/syd-start-your-dashboard/)
- [Témoignage client](https://cfd-innovation.fr/testimonial-schrader/)

