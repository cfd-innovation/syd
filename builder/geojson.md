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

## Correspondance données / zones

Pour que les données s'affichent correctement sur la carte, il faut une **correspondance** entre :
- Les valeurs de votre requête SQL (colonne de jointure)
- Les propriétés du fichier GeoJSON (code, nom, etc.)

### Exemple

**Requête SQL :**
```sql
SELECT code_departement, SUM(ventes) as total
FROM ventes_par_zone
GROUP BY code_departement
```

**Propriété GeoJSON :**
```json
{
  "properties": {
    "code": "75",
    "nom": "Paris"
  }
}
```

La correspondance se fait sur le champ `code` / `code_departement`.

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

