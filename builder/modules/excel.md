---
layout: default
title: Export Excel
parent: Modules
grand_parent: SYD Builder
nav_order: 3
---

# Export Excel
{: .fs-8 }

Configuration de l'export des données au format Excel
{: .fs-5 .fw-300 }

---

## Présentation

La fonctionnalité **Export Excel** permet aux utilisateurs du Visualizer de télécharger les données d'un module au format Excel (.xlsx).

---

## Activer l'export Excel

1. Ouvrez le formulaire de modification du module
2. Accédez à l'onglet **Excel**
3. Cochez la case **Bouton Excel**

Une fois activé, un bouton d'export apparaîtra sur le module dans le Visualizer.

---

## Requête d'export personnalisée

Par défaut, l'export utilise la même requête que le module. Cependant, vous pouvez définir une **requête spécifique** pour l'export Excel.

### Cas d'usage

- **Plus de colonnes** : Exporter des données supplémentaires non affichées dans le graphique
- **Plus de lignes** : Exporter toutes les données sans limite (le graphique peut n'afficher qu'un échantillon)
- **Format différent** : Formater les données différemment pour l'export

### Configuration

Dans le champ **Requête pour l'export Excel**, saisissez la requête SQL qui sera exécutée lors de l'export :

```sql
SELECT 
    date_vente,
    client,
    produit,
    quantite,
    prix_unitaire,
    quantite * prix_unitaire as total,
    region,
    commercial
FROM ventes
WHERE YEAR(date_vente) = 2024
ORDER BY date_vente DESC
```

{: .note }
> La requête d'export peut inclure plus de colonnes et de détails que la requête d'affichage du module.

---

## Paramètres de formulaire

La requête d'export prend en compte les mêmes paramètres de formulaire que la requête principale.

```sql
SELECT * FROM ventes
WHERE date_vente BETWEEN '{{date_debut}}' AND '{{date_fin}}'
  AND region = '{{region}}'
```

Les valeurs sélectionnées dans le formulaire du dashboard seront utilisées.

---

## Comportement dans le Visualizer

### Bouton d'export

Lorsque l'export est activé, un bouton Excel apparaît dans la barre d'outils du module :

- **Icône** : Icône Excel
- **Action** : Téléchargement du fichier .xlsx

### Nom du fichier

Le fichier exporté est nommé selon le format :
```
[Titre du module]_[Date].xlsx
```

---

## Bonnes pratiques

### Performance

{: .warning }
> Les exports de gros volumes peuvent prendre du temps. Limitez les données si nécessaire.

- **Limitez les lignes** : Utilisez des filtres ou LIMIT pour les gros volumes
- **Optimisez la requête** : Assurez-vous que la requête d'export est performante
- **Testez** : Vérifiez les temps d'export avec des données réelles

### Contenu

- **Nommez les colonnes** : Utilisez des alias explicites pour les en-têtes Excel
- **Formatez les dates** : Exportez les dates dans un format reconnu par Excel
- **Types de données** : Les nombres et dates seront correctement typés dans Excel

### Exemples de bonnes requêtes d'export

**Avec alias explicites :**
```sql
SELECT 
    date_commande as "Date de commande",
    client_nom as "Nom du client",
    montant_ht as "Montant HT",
    tva as "TVA",
    montant_ttc as "Montant TTC"
FROM commandes
```

**Avec formatage de date :**
```sql
SELECT 
    DATE_FORMAT(date_creation, '%d/%m/%Y') as "Date",
    libelle as "Libellé",
    montant as "Montant"
FROM transactions
```

