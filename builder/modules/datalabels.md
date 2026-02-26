---
layout: default
title: Datalabels
parent: Modules
grand_parent: SYD Builder
nav_order: 2
---

# Datalabels
{: .fs-8 }

Configuration des étiquettes de données sur les graphiques
{: .fs-5 .fw-300 }

---

## Présentation

Les **Datalabels** (étiquettes de données) permettent d'afficher les valeurs directement sur les éléments des graphiques (barres, points, portions de camembert...).

---

## Activer les Datalabels

1. Ouvrez le formulaire de modification du module
2. Accédez à l'onglet **Datalabels**
3. Cochez la case **Afficher**

Une fois activé, les options de personnalisation deviennent accessibles.

---

## Options de configuration

### Anchor (Ancrage)

Définit le point d'ancrage de l'étiquette par rapport à l'élément du graphique.

| Valeur | Description |
|:-------|:------------|
| **CENTER** | Au centre de l'élément |
| **START** | Au début de l'élément (bas pour les barres) |
| **END** | À la fin de l'élément (haut pour les barres) |

### Align (Alignement)

Définit l'alignement de l'étiquette par rapport à son point d'ancrage.

| Valeur | Description |
|:-------|:------------|
| **CENTER** | Centré sur l'ancrage |
| **TOP** | Au-dessus de l'ancrage |
| **RIGHT** | À droite de l'ancrage |
| **BOTTOM** | En-dessous de l'ancrage |
| **LEFT** | À gauche de l'ancrage |

### Offset (Décalage)

Distance en pixels entre l'étiquette et son point d'ancrage.

| Paramètre | Type | Défaut |
|:----------|:-----|:-------|
| **Offset** | Nombre (px) | 0 |

### Police

| Paramètre | Description | Défaut |
|:----------|:------------|:-------|
| **Font size** | Taille de la police en pixels | 15 |
| **Italique** | Afficher en italique | Non |
| **Bold** | Afficher en gras | Non |

---

## Exemples de configuration

### Graphique en barres - Valeurs au-dessus

```
Anchor: END
Align: TOP
Offset: 5
```

### Camembert - Valeurs au centre

```
Anchor: CENTER
Align: CENTER
Offset: 0
```

### Barres horizontales - Valeurs à droite

```
Anchor: END
Align: RIGHT
Offset: 10
```

---

## Bonnes pratiques

{: .note }
> Les datalabels augmentent la lisibilité mais peuvent surcharger le graphique si trop de données sont affichées.

### Recommandations

- **Peu de données** : Activez les datalabels pour les graphiques avec peu de points
- **Beaucoup de données** : Désactivez les datalabels et utilisez les tooltips (survol)
- **Taille de police** : Adaptez la taille selon l'espace disponible
- **Contraste** : Assurez-vous que les valeurs sont lisibles sur le fond

### Cas où éviter les datalabels

- Graphiques en courbes avec beaucoup de points
- Camemberts avec de très petites portions
- Barres groupées avec de nombreuses séries

