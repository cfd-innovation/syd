---
layout: default
title: GeoJSON
parent: SYD Builder
nav_order: 7
permalink: /builder/geojson/
---

# GeoJSON
{: .fs-8 }

Gestion des données géographiques pour les cartes
{: .fs-5 .fw-300 }

---

## Présentation

Les fichiers **GeoJSON** sont des fichiers de données géographiques utilisés par les modules de type **Map**. Ils définissent les contours des zones (pays, régions, départements, communes...) sur lesquelles les données seront affichées.

---

## Qu'est-ce que le GeoJSON ?

Le GeoJSON est un format ouvert de données géospatiales basé sur JSON. Il permet de représenter :
- Des **points** (villes, adresses)
- Des **lignes** (routes, frontières)
- Des **polygones** (régions, pays)

### Exemple de structure

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "code": "75",
        "nom": "Paris"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[2.25, 48.82], [2.42, 48.82], ...]]
      }
    }
  ]
}
```

---

## Importer un fichier GeoJSON

### Accès

1. Dans le menu, cliquez sur **GeoJSON**
2. Cliquez sur **Nouveau**

### Configuration

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Label** | Nom du jeu de données | `Départements France` |
| **Fichier** | Fichier GeoJSON à importer | `departements.geojson` |

### Étapes

1. Saisissez un **label** explicite
2. Sélectionnez le **fichier GeoJSON** depuis votre ordinateur
3. Cliquez sur **Valider**

---

## Utilisation dans les modules Map

Une fois importé, le fichier GeoJSON peut être associé à un module de type **Map** :

1. Créez ou modifiez un module de type **Map**
2. Dans les options (onglet Utilities), sélectionnez le GeoJSON à utiliser
3. La carte affichera les zones définies dans le fichier

---

## Sources de fichiers GeoJSON

### Ressources recommandées

| Source | Description | URL |
|:-------|:------------|:----|
| **Natural Earth** | Données mondiales | [naturalearthdata.com](https://www.naturalearthdata.com/) |
| **OpenDataSoft** | Données France | [data.opendatasoft.com](https://data.opendatasoft.com/) |
| **Geo.data.gouv.fr** | Données administratives France | [geo.data.gouv.fr](https://geo.data.gouv.fr/) |
| **GeoJSON.io** | Créer/éditer des GeoJSON | [geojson.io](https://geojson.io/) |

### Fichiers courants pour la France

- Régions (13 nouvelles régions)
- Départements (101)
- Communes
- EPCI (intercommunalités)

---

## Correspondance données / zones (Mapping)

Pour que les données s'affichent correctement sur la carte, il est essentiel de configurer la **correspondance** entre les résultats de votre requête SQL et les zones définies dans le fichier GeoJSON.

### Principe du mapping

Le système utilise une **clé de correspondance** pour associer chaque valeur de votre requête à une zone géographique :

| Côté Requête SQL | Côté GeoJSON |
|:-----------------|:-------------|
| Colonne `X` (alias obligatoire) | Propriété du GeoJSON (configurable) |
| Colonne `Y` (alias obligatoire) | Valeur à afficher sur la carte |

### Configuration dans les Utilities

Dans l'onglet **Utilities** d'un module de type Map, le champ **Nom de la propriété du geojson** définit quelle propriété du fichier GeoJSON sera utilisée pour faire la correspondance.

{: .important }
> La valeur de ce champ doit correspondre **exactement** au nom d'une propriété présente dans le fichier GeoJSON (sensible à la casse).

### Format de la requête SQL

La requête doit retourner **deux colonnes** avec les alias `X` et `Y` :

| Alias | Description | Rôle |
|:------|:------------|:-----|
| `X` | Clé de correspondance | Doit correspondre à la valeur de la propriété GeoJSON |
| `Y` | Valeur numérique | Valeur affichée et utilisée pour la coloration |

```sql
SELECT code_zone AS X, SUM(montant) AS Y
FROM ma_table
GROUP BY code_zone
```

{: .warning }
> Les alias `X` et `Y` sont **obligatoires** et sensibles à la casse (majuscules).

### Structure du fichier GeoJSON

Chaque zone (feature) du fichier GeoJSON possède des **propriétés** (properties) qui peuvent servir de clé de correspondance :

```json
{
  "type": "Feature",
  "properties": {
    "code": "75",
    "nom": "Paris",
    "region": "Île-de-France"
  },
  "geometry": { ... }
}
```

Dans cet exemple, vous pouvez utiliser `code`, `nom` ou `region` comme propriété de correspondance.

### Exemple complet

#### 1. Fichier GeoJSON (départements)

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "code": "75",
        "nom": "Paris"
      },
      "geometry": { ... }
    },
    {
      "type": "Feature",
      "properties": {
        "code": "69",
        "nom": "Rhône"
      },
      "geometry": { ... }
    }
  ]
}
```

#### 2. Configuration dans les Utilities

| Champ | Valeur |
|:------|:-------|
| Choix du GeoJSON | `Départements France` |
| Nom de la propriété du geojson | `code` |
| Choix du jeu de couleur | `Bleu` |

#### 3. Requête SQL

```sql
SELECT code_departement AS X, SUM(ventes) AS Y
FROM ventes_par_zone
GROUP BY code_departement
```

#### 4. Résultat

| X | Y |
|:--|--:|
| 75 | 15000 |
| 69 | 12500 |

Le système fait correspondre :
- `X = 75` → `properties.code = "75"` → Zone Paris colorée selon la valeur 15000
- `X = 69` → `properties.code = "69"` → Zone Rhône colorée selon la valeur 12500

### Jeux de couleurs disponibles

| Couleur | Code | Dégradé |
|:--------|:-----|:--------|
| **Rouge** | `red` | Du blanc au rouge foncé |
| **Vert** | `green` | Du blanc au vert foncé |
| **Bleu** | `blue` | Du blanc au bleu foncé |

L'intensité de la couleur varie en fonction de la valeur `Y` : les valeurs plus élevées apparaissent dans des teintes plus foncées.

### Résolution des problèmes courants

| Problème | Cause probable | Solution |
|:---------|:---------------|:---------|
| Zones non colorées | Pas de correspondance trouvée | Vérifier que les valeurs de `X` correspondent exactement aux valeurs de la propriété GeoJSON |
| Erreur d'affichage | Alias incorrects | S'assurer que les colonnes sont nommées `X` et `Y` (majuscules) |
| Aucune donnée | Propriété incorrecte | Vérifier le nom de la propriété dans les utilities et dans le fichier GeoJSON |

{: .note }
> Pour vérifier les propriétés disponibles dans votre fichier GeoJSON, ouvrez-le sur [geojson.io](https://geojson.io/) et cliquez sur une zone pour voir ses propriétés.

---

## Bonnes pratiques

### Taille des fichiers

{: .warning }
> Les fichiers GeoJSON volumineux peuvent ralentir l'affichage des cartes.

- **Simplifiez** les géométries si nécessaire (outil [mapshaper.org](https://mapshaper.org/))
- **Limitez** les propriétés aux champs nécessaires
- **Optimisez** pour le web (précision réduite)

### Nommage

- Utilisez des labels explicites : `Départements France 2024`
- Indiquez le niveau géographique : région, département, commune...

### Vérification

Avant l'import, vérifiez votre fichier :
1. Validité JSON
2. Affichage correct sur [geojson.io](https://geojson.io/)
3. Présence des propriétés nécessaires

