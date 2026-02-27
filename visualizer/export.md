---
layout: default
title: Export des données
parent: SYD Visualizer
nav_order: 3
---

# Export des données
{: .fs-8 }

Téléchargement des données au format Excel
{: .fs-5 .fw-300 }

---

## Présentation

SYD Visualizer permet d'exporter les données des modules au format **Excel (.xlsx)**. Cette fonctionnalité doit être activée par l'administrateur pour chaque module.

---

## Exporter les données d'un module

### Prérequis

- Le module doit avoir l'option **Export Excel** activée
- L'icône Excel doit être visible dans la barre d'outils du module

### Étapes

1. Repérez l'**icône Excel** (![Icone excel]({{ site.baseurl }}/assets/img/visualizer/icone_excel.png)) dans la barre d'outils du module
2. Cliquez sur l'icône
3. Le fichier se télécharge automatiquement

---

## Format du fichier exporté

### Nom du fichier

Le fichier est nommé automatiquement :
```
[Titre du module].xlsx
```

Exemple : `Ventes_mensuelles.xlsx`

### Contenu

Le fichier Excel contient :
- Les **en-têtes de colonnes** (première ligne)
- Les **données** correspondant aux filtres actifs
  - Si une requête d'export spécifique n'a pas été spécifiée dans le builder.
- Les valeurs sont **typées** (nombres, dates, textes)

---

## Données exportées

### Respect des filtres

{: .important }
> L'export prend en compte les filtres actuellement appliqués sur le dashboard.

Si vous avez filtré sur :
- Période : janvier à mars 2026
- Région : Nord

L'export ne contiendra que les données correspondant à ces critères.

### Requête d'export

L'administrateur peut configurer une **requête d'export spécifique** différente de la requête d'affichage. Cela permet :

- D'inclure **plus de colonnes** dans l'export
- D'exporter **toutes les données** (sans limitation d'affichage)
- De **formater différemment** les données pour Excel

---

## Cas d'usage

### Export simple

Pour une analyse rapide :
1. Appliquez vos filtres
2. Exportez le module
3. Ouvrez dans Excel pour analyse

### Export pour reporting

Pour un rapport périodique :
1. Configurez les filtres (période, périmètre)
2. Exportez les modules nécessaires
3. Intégrez dans votre rapport

### Export pour vérification

Pour valider les données affichées :
1. Exportez le module
2. Comparez avec vos données sources
3. Vérifiez les calculs

---

## Dépannage

| Problème | Solution |
|:---------|:---------|
| Pas d'icône Excel | L'export n'est pas activé pour ce module |
| Fichier vide | Vérifiez les filtres (peut-être trop restrictifs) |
| Données incomplètes | La requête d'export peut être limitée |
| Erreur au téléchargement | Rechargez la page et réessayez |

---

## Export des graphiques multi-séries

Lorsqu'un module graphique contient **plusieurs séries de données**, l'export Excel génère automatiquement **une feuille par série**.

### Organisation du fichier Excel

| Élément | Description |
|:--------|:------------|
| **Nombre de feuilles** | Une feuille par série du graphique |
| **Nom des feuilles** | Chaque feuille porte le **nom de la série** correspondante |
| **Contenu** | Les données spécifiques à chaque série |

### Exemple

Pour un graphique affichant les ventes par région (Nord, Sud, Est, Ouest), le fichier Excel contiendra 4 feuilles :
- Feuille "Nord" → données de la série Nord
- Feuille "Sud" → données de la série Sud
- Feuille "Est" → données de la série Est
- Feuille "Ouest" → données de la série Ouest

![Exemple graphique multi-séries Excel]({{ site.baseurl }}/assets/img/visualizer/graphique_multi_series.png)
![Exemple export multi-séries Excel]({{ site.baseurl }}/assets/img/visualizer/export_excel_multi_series.png)

{: .note }
> Cette organisation facilite l'analyse individuelle de chaque série tout en conservant l'ensemble des données dans un seul fichier.

---

## Limites

{: .warning }
> L'export de gros volumes peut prendre du temps. Soyez patient.

### Volumes importants

- Les exports volumineux peuvent nécessiter quelques secondes
- Évitez de cliquer plusieurs fois sur le bouton d'export
- En cas de timeout, contactez l'administrateur

### Données sensibles

Les données exportées sont soumises aux mêmes règles de confidentialité que les données affichées. Ne diffusez pas les exports sans autorisation appropriée.

