---
layout: default
title: SYD Builder
nav_order: 2
has_children: true
permalink: /builder/
---

# SYD Builder
{: .fs-9 }

Interface de conception des tableaux de bord
{: .fs-6 .fw-300 }

---

## Présentation

**SYD Builder** est l'interface d'administration destinée aux informaticiens et développeurs. Elle permet de :

- **Configurer les sources de données** : connexions aux bases de données
- **Créer des requêtes** : écrire et tester les requêtes SQL qui alimenteront les modules
- **Concevoir des modules** : créer des visualisations (graphiques, tableaux, indicateurs...)
- **Assembler des dashboards** : disposer les modules sur une grille flexible
- **Gérer les accès** : créer des utilisateurs et des groupes, attribuer des permissions
- **Configurer des formulaires** : créer des filtres interactifs pour les dashboards

---

## Menu principal

L'interface Builder propose les sections suivantes dans sa barre de navigation :

| Section | Description |
|:--------|:------------|
| **Connecteurs** | Configuration des sources de données |
| **Modules** | Liste et gestion des modules de visualisation |
| **Dashboards** | Liste et gestion des tableaux de bord |
| **Utilisateurs** | Gestion des utilisateurs |
| **Formulaires** | Création de formulaires de filtrage |
| **GeoJSON** | Gestion des fichiers de cartographie |
| **Licence** | Gestion de la licence Trial - Essential - Ultimate de SYD |
| **Paramètres** | Configuration générale |
| **Déconnexion** | Déconnexion de SYD Builder |

---

## Workflow de création d'un dashboard

```mermaid
graph TD
    A[1. Créer ou identifier un connecteur BDD] --> B[2. Créer des requêtes SQL]
    B --> C[3. Créer des modules]
    C --> D[4. Créer un dashboard]
    D --> E[5. Positionner les modules]
    E --> F[6. Attribuer les utilisateurs]
    F --> G[Dashboard prêt !]
```

### Étapes détaillées

1. **Connecteur** : Configurez la connexion à votre base de données source
2. **Requêtes** : Construisez les requêtes SQL qui extrairont les données
3. **Modules** : Créez les visualisations en associant requêtes et types de graphiques
4. **Dashboard** : Créez un nouveau tableau de bord en choisissant les modules, les utilisateurs/groupes autorisés et les formulaires attachés. 
5. **Layout** : Positionnez et redimensionnez les modules sur la grille


---

## Accès au Builder

L'accès à SYD Builder nécessite une authentification avec un compte disposant des droits d'administration.

{: .warning }
> L'interface Builder ne doit être accessible qu'aux personnes habilitées à concevoir et modifier les tableaux de bord.

