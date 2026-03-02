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

## Annotation ligne

L'annotation ligne permet d'afficher une **ligne horizontale** sur un graphique, représentant un seuil, un objectif ou une valeur de référence. Cette fonctionnalité est particulièrement utile pour visualiser des cibles à atteindre ou des limites à ne pas dépasser.

### Types de graphiques compatibles

| Type de graphique | Compatible |
|:------------------|:-----------|
| **Line** | ✅ Oui |
| **Bar** | ✅ Oui |
| Horizontal Bar | ❌ Non |
| Pie | ❌ Non |
| Doughnut | ❌ Non |

### Activation

Pour activer l'annotation ligne :
1. Accédez à l'onglet **Utilities** du formulaire de module
2. Cochez l'option **Afficher** dans la section "Annotation ligne"

### Paramètres de configuration

| Paramètre | Description | Type |
|:----------|:------------|:-----|
| **Valeur** | Position de la ligne sur l'axe Y | Nombre (décimal autorisé) |
| **Largeur** | Épaisseur de la ligne en pixels | Nombre entier |
| **Couleur** | Couleur de la ligne | Sélecteur de couleur |


![Annotation Line statique Utilities]({{ site.baseurl }}/assets/img/builder/Builder_annotation_line_statique.png)

### Mode dynamique

L'annotation ligne peut être **dynamique**, c'est-à-dire calculée à partir d'une requête SQL.

Pour activer le mode dynamique :
1. Cochez l'option **Dynamique**
2. Saisissez une requête SQL dans le champ **Requête**

{: .important }
> La requête doit retourner une **unique valeur** portant obligatoirement le nom `line`.

![Annotation Line dynamique Utilities]({{ site.baseurl }}/assets/img/builder/Builder_annotation_line_dynamique.png)

#### Exemple de requête dynamique

```sql
SELECT AVG(montant) AS line FROM ventes WHERE annee = :annee
```

{: .note }
> Les paramètres du dashboard (filtres) peuvent être utilisés dans la requête dynamique avec la même syntaxe que pour les requêtes standards (`:nom_parametre`).

### Cas d'utilisation courants

- **Objectif de vente** : Ligne représentant le chiffre d'affaires cible
- **Seuil d'alerte** : Limite à ne pas dépasser (coût, consommation...)
- **Moyenne** : Valeur moyenne calculée dynamiquement
- **Budget** : Ligne de référence budgétaire

### Limitations

{: .warning }
> L'annotation ligne nécessite que l'axe Y commence à **zéro** (valeur minimum = 0). Si l'axe Y commence à une autre valeur, la ligne ne sera pas affichée correctement.

---

## Jauge (Gauge)

La jauge est un type de module permettant d'afficher une valeur unique sous forme d'un indicateur semi-circulaire avec une aiguille. L'onglet **Utilities** permet de configurer les sections et les couleurs de la jauge.

### Sections de la jauge

{: .highlight }
> **Champ obligatoire**

Les sections définissent les **bornes supérieures** de chaque zone de la jauge. Les valeurs doivent être séparées par des virgules.

| Paramètre | Description | Format |
|:----------|:------------|:-------|
| **Sections** | Liste des valeurs maximales de chaque section | Nombres séparés par des virgules |

#### Exemple

Pour une jauge avec 4 sections (0-25, 25-50, 50-75, 75-100) :

```
25,50,75,100
```

{: .note }
> Si aucune section n'est définie, la valeur par défaut `25,50,75,100` est utilisée.

### Couleurs de la jauge

Les couleurs définissent l'apparence de chaque section. L'ordre des couleurs correspond à l'ordre des sections.

| Paramètre | Description | Format |
|:----------|:------------|:-------|
| **Couleurs** | Liste des couleurs de chaque section | Noms ou codes couleur séparés par des virgules |

#### Formats de couleurs acceptés

- **Noms de couleurs** : `green`, `yellow`, `orange`, `red`
- **Codes hexadécimaux** : `#00FF00`, `#FFFF00`, `#FFA500`, `#FF0000`

#### Exemple

Pour des couleurs vert → jaune → orange → rouge :

```
green,yellow,orange,red
```

Ou avec des codes hexadécimaux :

```
#28a745,#ffc107,#fd7e14,#dc3545
```

{: .note }
> Si aucune couleur n'est définie, les couleurs par défaut `green`, `yellow`, `orange`, `red` sont utilisées.

### Correspondance sections/couleurs

Le nombre de couleurs doit correspondre au nombre de sections pour un rendu optimal :

| Sections | Couleurs | Résultat |
|:---------|:---------|:---------|
| `25,50,75,100` | `green,yellow,orange,red` | 4 zones colorées |
| `50,100` | `green,red` | 2 zones colorées |
| `33,66,100` | `#00FF00,#FFFF00,#FF0000` | 3 zones colorées |


![Jauge Utilities]({{ site.baseurl }}/assets/img/builder/Builder_jauge_utilities.png)

### Cas d'utilisation courants

- **Indicateur de performance** : Vert (bon) → Rouge (mauvais)
- **Niveau de charge** : Bleu (faible) → Rouge (élevé)
- **Score qualité** : Sections à 60, 80, 100 avec couleurs rouge, orange, vert

---

## Barre de progression (Progress)

La barre de progression permet d'afficher une valeur sous forme d'une barre horizontale indiquant un pourcentage d'avancement ou de remplissage. L'onglet **Utilities** permet de configurer les bornes, l'affichage et la couleur de la barre.

### Valeurs minimum et maximum

Ces paramètres définissent l'échelle de la barre de progression.

| Paramètre | Description | Valeur par défaut |
|:----------|:------------|:------------------|
| **Valeur minimum** | Borne inférieure de l'échelle | 0 |
| **Valeur maximum** | Borne supérieure de l'échelle | 100 |

{: .note }
> Le pourcentage de remplissage est calculé automatiquement : `(valeur - min) / (max - min) × 100`

#### Exemple

Pour une barre représentant un objectif de 500 unités avec un minimum de 0 :
- **Valeur minimum** : `0`
- **Valeur maximum** : `500`

Si la valeur retournée par la requête est 250, la barre sera remplie à 50%.

### Options d'affichage

Deux options permettent de contrôler l'affichage du texte sur la barre :

| Option | Description |
|:-------|:------------|
| **Label** | Affiche la valeur sur la barre de progression |
| **Pourcentage** | Affiche la valeur en pourcentage (avec le symbole %) |

#### Combinaisons possibles

| Label | Pourcentage | Affichage |
|:------|:------------|:----------|
| ❌ | ❌ | Aucun texte |
| ✅ | ❌ | Valeur brute (ex: `250`) |
| ✅ | ✅ | Pourcentage (ex: `50.00%`) |
| ❌ | ✅ | Aucun texte |

{: .note }
> L'option **Pourcentage** n'a d'effet que si **Label** est également coché.

### Couleur de la barre

| Paramètre | Description | Format |
|:----------|:------------|:-------|
| **Couleur** | Couleur de remplissage de la barre | Sélecteur de couleur |

La couleur peut être choisie via le sélecteur de couleur intégré ou saisie directement en code hexadécimal.

### Cas d'utilisation courants

- **Avancement de projet** : Min 0, Max 100 avec affichage en pourcentage
- **Objectif de vente** : Min 0, Max (objectif) avec affichage de la valeur brute
- **Capacité de stockage** : Min 0, Max (capacité totale) avec couleur d'alerte si proche du max
- **Score de satisfaction** : Min 0, Max 10 ou 100 selon l'échelle utilisée

![Progression Bar Utilities]({{ site.baseurl }}/assets/img/builder/Builder_progress_bar_utilities.png)

---

## Indicateur (Indicator)

L'indicateur est un module permettant d'afficher une valeur unique de manière mise en avant, avec un formatage personnalisé et des options de mise en forme conditionnelle. L'onglet **Utilities** offre de nombreuses possibilités de personnalisation.

### Couleurs de base

| Paramètre | Description | Format |
|:----------|:------------|:-------|
| **Couleur de fond** | Couleur d'arrière-plan du module | Sélecteur de couleur (défaut : blanc) |
| **Couleur du texte** | Couleur de la valeur affichée | Sélecteur de couleur |

### Texte personnalisé

Le champ **Texte** permet de définir le format d'affichage de la valeur. Le caractère `%` représente la valeur retournée par la requête.

| Paramètre | Description |
|:----------|:------------|
| **Texte** | Format d'affichage avec `%` comme placeholder pour la valeur |

#### Exemples de formats

| Texte saisi | Valeur retournée | Affichage |
|:------------|:-----------------|:----------|
| `%` | 1234 | `1234` |
| `% €` | 1234 | `1234 €` |
| `Total : %` | 1234 | `Total : 1234` |
| `% unités vendues` | 1234 | `1234 unités vendues` |

{: .note }
> Pour afficher le caractère `%` littéralement sans qu'il soit remplacé par la valeur, utilisez `/%`.

### Formatage des nombres

Ces options permettent de contrôler l'affichage numérique de la valeur.

| Paramètre | Description | Valeur par défaut |
|:----------|:------------|:------------------|
| **Nombre de décimales** | Nombre de chiffres après la virgule | 0 |
| **Séparateur de décimales** | Caractère séparant les décimales | `,` |
| **Séparateur de milliers** | Caractère séparant les milliers | ` ` (espace) |

#### Exemples de formatage

| Valeur brute | Décimales | Séparateur décimal | Séparateur milliers | Résultat |
|:-------------|:----------|:-------------------|:--------------------|:---------|
| 1234567.89 | 2 | `,` | ` ` | `1 234 567,89` |
| 1234567.89 | 0 | `,` | ` ` | `1 234 568` |
| 1234567.89 | 2 | `.` | `,` | `1,234,567.89` |

### Styles de texte

Trois options de style peuvent être combinées :

| Option | Description | Code interne |
|:-------|:------------|:-------------|
| **Italic** | Texte en italique | `I` |
| **Gras** | Texte en gras | `B` |
| **Souligné** | Texte souligné | `U` |

{: .note }
> Ces options peuvent être combinées librement (ex: gras et souligné).

### Mise en forme conditionnelle

La mise en forme conditionnelle permet de **modifier dynamiquement l'apparence** de l'indicateur en fonction de la valeur affichée. C'est une fonctionnalité puissante pour créer des alertes visuelles.

#### Ajouter une condition

Cliquez sur le bouton **+** pour ajouter une nouvelle condition. Chaque condition comprend :

| Paramètre | Description |
|:----------|:------------|
| **Opération** | Type de comparaison à effectuer |
| **Zone à colorer** | Élément à modifier (valeur ou fond) |
| **Valeur** | Seuil de comparaison |
| **Couleur** | Couleur à appliquer si la condition est vraie |

#### Opérations disponibles

| Opération | Description | Symbole |
|:----------|:------------|:--------|
| **Supérieur** | Valeur strictement supérieure au seuil | `>` |
| **Supérieur ou égal** | Valeur supérieure ou égale au seuil | `>=` |
| **Inférieur** | Valeur strictement inférieure au seuil | `<` |
| **Inférieur ou égal** | Valeur inférieure ou égale au seuil | `<=` |
| **Égal** | Valeur exactement égale au seuil | `=` |

#### Zones à colorer

| Zone | Description |
|:-----|:------------|
| **Valeur** | Change la couleur du texte de la valeur |
| **Background** | Change la couleur de fond du module |

#### Ordre d'évaluation

{: .important }
> Les conditions sont évaluées **dans l'ordre de définition**. Dès qu'une condition est vraie, elle est appliquée et les suivantes sont ignorées.

#### Exemple de configuration

Pour un indicateur affichant un taux de satisfaction :

| Condition | Opération | Valeur | Zone | Couleur |
|:----------|:----------|:-------|:-----|:--------|
| 1 | Inférieur | 50 | Background | Rouge |
| 2 | Inférieur | 75 | Background | Orange |
| 3 | Supérieur ou égal | 75 | Background | Vert |

Avec cette configuration :
- Valeur < 50 → Fond rouge
- 50 ≤ Valeur < 75 → Fond orange
- Valeur ≥ 75 → Fond vert

{: .note }
> Les couleurs définies dans les conditions **surchargent** les couleurs de base définies plus haut.

### Cas d'utilisation courants

- **KPI financier** : Chiffre d'affaires avec formatage milliers et symbole €
- **Taux de conversion** : Pourcentage avec 2 décimales et mise en forme conditionnelle
- **Alerte stock** : Quantité en rouge si inférieure au seuil minimum
- **Score NPS** : Mise en forme conditionnelle vert/orange/rouge selon le score

---

![Indicator Utilities]({{ site.baseurl }}/assets/img/builder/Builder_indicator_utilities.png)

## Bonnes pratiques

### Choix du thème de couleurs

- **Accessibilité** : Choisissez des thèmes avec un bon contraste de couleurs
- **Cohérence** : Utilisez le même thème pour les modules d'un même dashboard
- **Lisibilité** : Évitez les thèmes avec trop de couleurs similaires pour les petits jeux de données

### Dimensions

- **Proportions** : Adaptez les proportions au contenu (les tableaux ont besoin de plus de largeur)
- **Responsive** : Testez l'affichage sur différentes tailles d'écran
- **Équilibre** : Répartissez harmonieusement les modules sur le dashboard

