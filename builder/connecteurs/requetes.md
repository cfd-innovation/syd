---
layout: default
title: Requêtes SQL
parent: Connecteurs
grand_parent: SYD Builder
nav_order: 3
---

# Requêtes SQL
{: .fs-8 }

Inventaire des requêtes SQL configurées dans SYD
{: .fs-5 .fw-300 }

---

## Présentation

La section **Requêtes SQL** n'est pas une source de données à proprement parler, mais un **inventaire centralisé** de toutes les requêtes SQL configurées dans SYD.

Ces requêtes peuvent être créées de deux manières :
- Via le **Requêtes Builder** (éditeur visuel)
- Directement depuis la configuration des **modules**

{: .note }
> L'avantage de cet inventaire est de pouvoir **réutiliser une même requête dans plusieurs modules**, évitant ainsi la duplication et facilitant la maintenance.

---

## Accéder à l'inventaire

1. Dans le menu **Connecteurs**, sélectionnez **Requêtes**
2. La liste de toutes les requêtes configurées s'affiche

---

## Informations affichées

Pour chaque requête de l'inventaire :

| Champ | Description |
|:------|:------------|
| **Label du jeu de données** | Nom identifiant la requête |
| **Base de données** | Connexion BDD utilisée |
| **Requête SQL** | Code SQL de la requête |

---

## Réutilisation des requêtes

Une requête créée peut être associée à plusieurs modules. Cela permet :

- **Cohérence** : Les mêmes données sont affichées de manière identique dans différents modules
- **Maintenance simplifiée** : Modifier la requête une seule fois met à jour tous les modules associés
- **Gain de temps** : Pas besoin de recréer la même requête pour chaque module

---

## Exemples de requêtes

### Requête simple - Comptage

```sql
SELECT 
    COUNT(*) as total 
FROM clients 
WHERE actif = 1
```

### Requête avec groupement - Pour graphiques

```sql
SELECT 
    DATE_FORMAT(date_vente, '%Y-%m') as mois,
    SUM(montant) as total_ventes
FROM ventes
WHERE YEAR(date_vente) = 2024
GROUP BY DATE_FORMAT(date_vente, '%Y-%m')
ORDER BY mois
```

### Requête avec paramètres de formulaire

```sql
SELECT 
    produit,
    quantite,
    prix_unitaire,
    quantite * prix_unitaire as total
FROM commandes
WHERE date_commande BETWEEN '{{date_debut}}' AND '{{date_fin}}'
  AND region = '{{region}}'
ORDER BY date_commande DESC
```

{: .note }
> Les paramètres entre doubles accolades `{{param}}` sont remplacés par les valeurs des champs de formulaire correspondants.

---

## Structure des données retournées

Pour les graphiques, la requête doit retourner des colonnes correspondant aux axes :

| Type de module | Colonnes attendues |
|:---------------|:-------------------|
| **Line, Bar** | 1 colonne X (labels) + N colonnes Y (valeurs) |
| **Pie, Doughnut** | 1 colonne labels + 1 colonne valeurs |
| **Table** | Toutes les colonnes souhaitées |
| **Indicator** | 1 valeur numérique |
| **Gauge, Progress** | 1 valeur numérique (pourcentage) |

### Exemple pour un graphique Line/Bar

```sql
SELECT 
    mois,           -- Axe X (labels)
    ventes_2023,    -- Série 1
    ventes_2024     -- Série 2
FROM statistiques_mensuelles
ORDER BY mois
```

### Exemple pour un indicateur

```sql
SELECT SUM(montant) as chiffre_affaires
FROM ventes
WHERE YEAR(date_vente) = YEAR(CURRENT_DATE)
```

---

## Association requête-module

Une fois créée, la requête apparaît dans la liste des modules qui l'utilisent. Cette information s'affiche sous le champ de requête :

> *"Cette requête est utilisée dans les modules suivants : Module Ventes, Module CA..."*

{: .important }
> Toute modification d'une requête impacte tous les modules qui l'utilisent.

---

## Bonnes pratiques

### Performance

- **Limitez les données** : Utilisez `LIMIT` pour les requêtes de test
- **Indexez** : Assurez-vous que les colonnes de filtre sont indexées
- **Agrégez** : Préférez les agrégations côté base de données

### Lisibilité

- **Nommez les colonnes** : Utilisez des alias explicites (`AS nom_explicite`)
- **Formatez** : Indentez votre SQL pour une meilleure lisibilité
- **Commentez** : Ajoutez des commentaires pour les requêtes complexes

### Sécurité

- **Lecture seule** : Les requêtes doivent être en lecture (`SELECT`)
- **Pas de modification** : Évitez les `INSERT`, `UPDATE`, `DELETE`

---

## Dépannage

| Problème | Solution |
|:---------|:---------|
| Aucune donnée | Vérifiez les filtres et la période |
| Erreur de syntaxe | Testez la requête directement sur la BDD |
| Timeout | Optimisez la requête ou ajoutez des index |
| Colonnes manquantes | Vérifiez les alias et noms de colonnes |

