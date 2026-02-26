---
layout: default
title: Options d'affichage
parent: Modules
grand_parent: SYD Builder
nav_order: 1
---

# Options d'affichage
{: .fs-8 }

Configuration de l'apparence des modules
{: .fs-5 .fw-300 }

---

## Présentation

L'onglet **Affichage** du formulaire de module permet de configurer l'apparence visuelle : dimensions, thème de couleurs, position de la légende, mode sombre, etc.

---

## Dimensions

<!-- ![Dimensions du module]({{ site.baseurl }}/assets/img/builder/module-dimensions.png) -->

| Paramètre | Description | Valeurs |
|:----------|:------------|:--------|
| **Hauteur** | Hauteur relative du module | 0 à 100 |
| **Largeur** | Largeur relative du module | 0 à 100 |

{: .note }
> Les dimensions sont relatives à la grille du dashboard. La taille finale dépend du positionnement dans le layout.

---

## Thème de couleurs (Charts)

Pour les graphiques (Line, Bar, Pie, Doughnut, Horizontal Bar), vous pouvez sélectionner un **thème de couleurs** prédéfini.

Les thèmes sont fournis par la bibliothèque [chartjs-plugin-colorschemes](https://nagix.github.io/chartjs-plugin-colorschemes/).

### Catégories de thèmes disponibles

| Catégorie | Exemples |
|:----------|:---------|
| **Brewer** | Accent8, Dark2, Paired12, Set1... |
| **Office** | Excel, Office2007, Office2010... |
| **Tableau** | Tableau10, Tableau20, Classic10... |

### Prévisualisation

Consultez la galerie des thèmes sur le site officiel pour choisir celui qui convient à vos données :
[https://nagix.github.io/chartjs-plugin-colorschemes/](https://nagix.github.io/chartjs-plugin-colorschemes/)

---

## Légende

La légende affiche les libellés des séries de données. Sa position peut être configurée :

| Position | Description |
|:---------|:------------|
| **Pas de légende** | Légende masquée |
| **En haut** | Au-dessus du graphique |
| **En bas** | En-dessous du graphique |
| **À gauche** | À gauche du graphique |
| **À droite** | À droite du graphique |

{: .note }
> L'option de légende n'est disponible que pour les types de graphiques : Line, Bar, Horizontal Bar, Pie, Doughnut.

---

## Mode sombre (Dark mode)

Cochez l'option **Dark mode** pour appliquer un fond sombre au module.

| Mode | Fond | Texte |
|:-----|:-----|:------|
| **Normal** | Clair | Foncé |
| **Dark mode** | Sombre | Clair |

{: .important }
> Le mode sombre du module est indépendant du mode sombre du dashboard. Vous pouvez avoir des modules clairs sur un dashboard sombre et inversement.

---

## Options par type de module

### Graphiques (Line, Bar, Pie...)

- Thème de couleurs
- Position de la légende
- Dark mode

### Tableaux

- Largeur et hauteur
- Dark mode

### Indicateurs

- Largeur et hauteur
- Dark mode

### Maps

- Largeur et hauteur
- Fichier GeoJSON associé (via Utilities)

### Iframe

- Largeur et hauteur
- URL source (via Utilities)

---

## Bonnes pratiques

### Choix du thème de couleurs

- **Accessibilité** : Choisissez des thèmes avec un bon contraste de couleurs
- **Cohérence** : Utilisez le même thème pour les modules d'un même dashboard
- **Lisibilité** : Évitez les thèmes avec trop de couleurs similaires pour les petits jeux de données

### Dimensions

- **Proportions** : Adaptez les proportions au contenu (les tableaux ont besoin de plus de largeur)
- **Responsive** : Testez l'affichage sur différentes tailles d'écran
- **Équilibre** : Répartissez harmonieusement les modules sur le dashboard

