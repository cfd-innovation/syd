---
layout: default
title: Consultation des dashboards
parent: SYD Visualizer
nav_order: 2
---

# Consultation des dashboards
{: .fs-8 }

Navigation et interaction avec les tableaux de bord
{: .fs-5 .fw-300 }

---

## Navigation entre dashboards

### Menu de navigation

Après connexion, le menu de navigation affiche les dashboards auxquels vous avez accès, organisés par catégories.

<!-- ![Menu navigation]({{ site.baseurl }}/assets/img/visualizer/navigation.png) -->

### Accéder à un dashboard

1. Cliquez sur le **menu** ou l'**icône dashboard** dans la barre de navigation
2. Parcourez les **catégories** disponibles
3. Cliquez sur le **nom du dashboard** souhaité

### Dashboard par défaut

Si configuré, un dashboard s'affiche automatiquement après la connexion.

---

## Structure d'un dashboard

Un dashboard se compose de plusieurs éléments :

```
┌─────────────────────────────────────────────────────────────┐
│                    BARRE DE NAVIGATION                      │
├─────────────────────────────────────────────────────────────┤
│  Titre du Dashboard                                         │
│  Sous-titre                                                 │
├─────────────────────────────────────────────────────────────┤
│  [Formulaire de filtres - si configuré]                     │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │   Module 1   │  │   Module 2   │  │   Module 3   │       │
│  │              │  │              │  │              │       │
│  └──────────────┘  └──────────────┘  └──────────────┘       │
│  ┌─────────────────────────────────────────────────┐        │
│  │                    Module 4                      │        │
│  │                                                  │        │
│  └─────────────────────────────────────────────────┘        │
└─────────────────────────────────────────────────────────────┘
```

---

## Interaction avec les graphiques

### Survol (Tooltips)

Passez votre souris sur un élément d'un graphique pour afficher un **tooltip** avec les informations détaillées :

- Libellé de l'élément
- Valeur précise
- Pourcentage (pour les camemberts)
- Informations des séries multiples

### Légende interactive

La légende des graphiques est interactive :

| Action | Effet |
|:-------|:------|
| **Clic simple** sur une série | Masque/affiche la série |
| **Survol** d'une série | Met en évidence la série |

### Exemple

Pour un graphique avec les séries "Ventes 2023" et "Ventes 2024" :
- Cliquez sur "Ventes 2023" dans la légende pour masquer cette série
- Le graphique n'affiche plus que "Ventes 2024"
- Cliquez à nouveau pour réafficher "Ventes 2023"

---

## Types de modules

### Graphiques

| Type | Interaction |
|:-----|:------------|
| **Line** (courbes) | Tooltip au survol, légende cliquable |
| **Bar** (barres) | Tooltip au survol, légende cliquable |
| **Pie** (camembert) | Tooltip avec pourcentage |
| **Doughnut** (anneau) | Tooltip avec pourcentage |

### Tableaux

| Fonction | Description |
|:---------|:------------|
| **Tri** | Cliquez sur l'en-tête pour trier |
| **Recherche** | Utilisez le champ de recherche (si activé) |
| **Pagination** | Naviguez entre les pages |

### Indicateurs

Les indicateurs affichent une valeur clé. Pas d'interaction particulière.

### Cartes

| Interaction | Description |
|:------------|:------------|
| **Survol** | Affiche les infos de la zone |
| **Zoom** | Molette ou boutons +/- |
| **Déplacement** | Cliquer-glisser |

---

## Formulaires de filtres

Si le dashboard dispose de filtres :

### Utilisation

1. Les champs de filtre s'affichent en haut du dashboard
2. Modifiez les valeurs selon vos besoins
3. Cliquez sur le bouton **Appliquer** ou **Filtrer**
4. Tous les modules se mettent à jour avec les nouvelles données

### Types de filtres

| Type | Usage | Exemple |
|:-----|:------|:--------|
| **Texte** | Saisie libre | Recherche par nom |
| **Date** | Sélection de date | Période de début/fin |
| **Liste simple** | Un seul choix | Région |
| **Liste multiple** | Plusieurs choix | Plusieurs produits |

### Réinitialisation

Pour revenir aux valeurs par défaut, rechargez la page ou utilisez le bouton de réinitialisation (si disponible).

---

## Barre d'outils des modules

Chaque module peut disposer d'outils dans sa barre de titre :

| Icône | Fonction | Description |
|:------|:---------|:------------|
| 🔄 | **Refresh** | Rafraîchir les données du module |
| 📥 | **Excel** | Exporter les données en Excel |
| 🔍 | **Recherche** | Champ de recherche (tableaux) |

---

## Rafraîchissement des données

### Automatique

Certains modules peuvent se rafraîchir automatiquement à intervalle régulier (configuré par l'administrateur).

### Manuel

- **Module seul** : Cliquez sur l'icône Refresh du module
- **Dashboard complet** : Rechargez la page (F5)

---

## Responsive

L'interface s'adapte à la taille de l'écran :

- **Desktop** : Modules côte à côte selon le layout
- **Tablette** : Modules empilés ou réduits
- **Mobile** : Modules en pleine largeur, empilés

{: .note }
> Pour une meilleure expérience, l'utilisation sur écran large est recommandée pour les dashboards complexes.

