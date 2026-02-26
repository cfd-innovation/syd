---
layout: default
title: Layout
parent: Dashboards
grand_parent: SYD Builder
nav_order: 1
---

# Layout des modules
{: .fs-8 }

Positionnement et dimensionnement des modules sur le dashboard
{: .fs-5 .fw-300 }

---

## Présentation

L'écran de **Layout** permet de configurer la disposition des modules sur un dashboard :
- **Ordre d'affichage** : Réorganiser les modules par glisser-déposer
- **Dimensions** : Ajuster la hauteur et la largeur de chaque module

---

## Accéder au Layout

1. Dans la liste des dashboards, repérez le dashboard à modifier
2. Cliquez sur l'icône **Layout** (grille) dans les actions du dashboard

---

## Interface de configuration

<!-- ![Layout dashboard]({{ site.baseurl }}/assets/img/builder/dashboard-layout.png) -->

L'écran de layout affiche la liste des modules du dashboard. Chaque module dispose de :
- Une **poignée de déplacement** (icône flèches) pour réordonner
- Un **slider de hauteur** (0-100)
- Un **slider de largeur** (0-100)

---

## Réordonner les modules

### Glisser-déposer

1. Cliquez sur la **poignée** (icône flèches) d'un module
2. Maintenez le clic et **déplacez** le module vers sa nouvelle position
3. Relâchez pour valider la nouvelle position

L'ordre des modules dans la liste correspond à leur ordre d'affichage sur le dashboard :
- **Premier module** = En haut à gauche
- **Dernier module** = En bas

---

## Configurer les dimensions

### Hauteur et largeur

Les dimensions sont exprimées en **pourcentage** (0 à 100) et sont relatives à l'espace disponible.

| Paramètre | Description | Impact |
|:----------|:------------|:-------|
| **Hauteur** | Hauteur du module | Espace vertical occupé |
| **Largeur** | Largeur du module | Espace horizontal (sur la même ligne) |

### Utilisation des sliders

- **Slider** : Glissez pour ajuster visuellement
- **Champ numérique** : Saisissez une valeur précise

Les deux contrôles sont synchronisés : modifier l'un met à jour l'autre.

---

## Comportement de la grille

Le système de layout fonctionne en mode **flow** :
- Les modules se placent de gauche à droite
- Quand la ligne est pleine (largeur totale > 100%), le module passe à la ligne suivante
- Les modules s'adaptent à l'espace disponible

### Exemples de dispositions

**2 modules côte à côte :**
```
Module A : Largeur 50%
Module B : Largeur 50%
```

**3 modules égaux :**
```
Module A : Largeur 33%
Module B : Largeur 33%
Module C : Largeur 34%
```

**1 module pleine largeur + 2 petits :**
```
Module A : Largeur 100%
Module B : Largeur 50%
Module C : Largeur 50%
```

---

## Bonnes pratiques

### Équilibre visuel

- **Cohérence** : Utilisez des largeurs cohérentes (50/50, 33/33/34, etc.)
- **Hiérarchie** : Placez les informations importantes en haut et en grand
- **Respiration** : Évitez de surcharger avec trop de modules

### Responsive

{: .note }
> Sur les écrans mobiles, les modules peuvent s'empiler automatiquement.

- Testez l'affichage sur différentes tailles d'écran
- Privilégiez des modules pouvant s'adapter à différentes largeurs

### Types de modules

| Type | Largeur recommandée | Hauteur recommandée |
|:-----|:--------------------|:--------------------|
| **Indicateur** | 25-33% | 20-30% |
| **Graphique** | 50-100% | 40-60% |
| **Tableau** | 100% | 40-60% |
| **Map** | 50-100% | 50-70% |

---

## Valider les modifications

Une fois le layout configuré :

1. Cliquez sur **Valider** pour enregistrer
2. Les modifications sont immédiatement appliquées
3. Prévisualisez le résultat dans le Visualizer

