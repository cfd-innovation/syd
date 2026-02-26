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

1. Repérez l'**icône Excel** (📥) dans la barre d'outils du module
2. Cliquez sur l'icône
3. Le fichier se télécharge automatiquement

<!-- ![Bouton export Excel]({{ site.baseurl }}/assets/img/visualizer/export-excel.png) -->

---

## Format du fichier exporté

### Nom du fichier

Le fichier est nommé automatiquement :
```
[Titre du module]_[Date].xlsx
```

Exemple : `Ventes_mensuelles_2024-02-26.xlsx`

### Contenu

Le fichier Excel contient :
- Les **en-têtes de colonnes** (première ligne)
- Les **données** correspondant aux filtres actifs
- Les valeurs sont **typées** (nombres, dates, textes)

---

## Données exportées

### Respect des filtres

{: .important }
> L'export prend en compte les filtres actuellement appliqués sur le dashboard.

Si vous avez filtré sur :
- Période : janvier à mars 2024
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

## Limites

{: .warning }
> L'export de gros volumes peut prendre du temps. Soyez patient.

### Volumes importants

- Les exports volumineux peuvent nécessiter quelques secondes
- Évitez de cliquer plusieurs fois sur le bouton d'export
- En cas de timeout, contactez l'administrateur

### Données sensibles

Les données exportées sont soumises aux mêmes règles de confidentialité que les données affichées. Ne diffusez pas les exports sans autorisation appropriée.

