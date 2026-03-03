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

![Menu Visualizer]({{ site.baseurl }}/assets/img/visualizer/Menu_Visualizer.png)

### Accéder à un dashboard

1. Cliquez sur le **menu** ou l'**icône dashboard** dans la barre de navigation
2. Parcourez les **catégories** disponibles
3. Cliquez sur le **nom du dashboard** souhaité

### Dashboard par défaut

Si configuré côté builder, un dashboard s'affiche automatiquement après la connexion.

---

## Structure d'un dashboard

Un dashboard se compose de plusieurs éléments :

```
┌─────────────────────────────────────────────────────────────┐
│                    BARRE DE NAVIGATION                      │
├─────────────────────────────────────────────────────────────┤
│  Titre du Dashboard                                         │
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

![Tooltip Visualizer]({{ site.baseurl }}/assets/img/visualizer/Tooltip_visualizer.png)

### Légende interactive

La légende des graphiques est interactive :

| Action | Effet |
|:-------|:------|
| **Clic simple** sur une série | Masque/affiche la série |
| **Survol** d'une série | Met en évidence la série |

![Légendes Visualizer]({{ site.baseurl }}/assets/img/visualizer/Legendes_visualizer.png)

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

| Fonction | Description                                                   |
|:---------|:--------------------------------------------------------------|
| **Tri** | (Option à activer) Cliquez sur l'en-tête pour trier           |
| **Recherche** | (Option à activer) Utilisez le champ de recherche (si activé) |


![Tableau Visualizer]({{ site.baseurl }}/assets/img/visualizer/tableaux_visualizer.png)


### Indicateurs

Les indicateurs affichent une valeur clé. Pas d'interaction particulière.

![Indicateur Visualizer]({{ site.baseurl }}/assets/img/visualizer/Module_SYD_Visualizer.png)


### Cartes

| Interaction | Description |
|:------------|:------------|
| **Survol** | Affiche les infos de la zone |
| **Zoom** | Molette ou boutons +/- |
| **Déplacement** | Cliquer-glisser |


![Maps bubble Visualizer]({{ site.baseurl }}/assets/img/visualizer/maps_bubble_visualizer.png)
![Maps choroplèthes Visualizer]({{ site.baseurl }}/assets/img/visualizer/maps_choro_visualizer.png)


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
| **Liste simple** | Un seul choix | Région |
| **Liste multiple** | Plusieurs choix | Plusieurs produits |

![Filtres Visualizer]({{ site.baseurl }}/assets/img/visualizer/Filtres_visualizer.png)

### Mode compact des filtres

Les filtres peuvent être affichés en mode **compact** (réduit) pour gagner de l'espace sur le dashboard. Dans ce mode :

- Les filtres sont repliés et occupent moins de place
- Les **valeurs sélectionnées** s'affichent sous forme de **badges** directement visibles

{: .note }
> Le mode compact est particulièrement utile lorsque le dashboard contient de nombreux filtres ou pour maximiser l'espace d'affichage des modules.

![Filtres badge Visualizer]({{ site.baseurl }}/assets/img/visualizer/filtres_badge_visualizer.png)


---

## Barre d'outils des modules

Chaque module peut disposer d'outils dans sa barre de titre :

| Icône                                                                        | Fonction | Description |
|:-----------------------------------------------------------------------------|:---------|:------------|
| ![Icone refresh]({{ site.baseurl }}/assets/img/visualizer/icone_refresh.png) | **Refresh** | Rafraîchir les données du module |
| ![Icone excel]({{ site.baseurl }}/assets/img/visualizer/icone_excel.png)     | **Excel** | Exporter les données en Excel |
| ![Icone search]({{ site.baseurl }}/assets/img/visualizer/icone_search.png)   | **Recherche** | Champ de recherche (tableaux) |

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

