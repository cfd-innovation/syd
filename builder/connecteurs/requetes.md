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
    DATE_FORMAT(date_vente, '%Y-%m') as X,
    SUM(montant) as Y
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
WHERE date_commande BETWEEN '###date_debut###' AND '###date_fin###'
  AND region = '###region###'
ORDER BY date_commande DESC
```

ou pour les valeurs multiples : 

```sql
SELECT 
    produit,
    quantite,
    prix_unitaire,
    quantite * prix_unitaire as total
FROM commandes
WHERE region IN '&&&region&&&'
ORDER BY date_commande DESC
```

{: .note }
> Les paramètres entre triples dièses `###param###` sont remplacés par les valeurs des champs de formulaire correspondants.
> Les paramètres entre triples & `&&&param&&&` sont remplacés par les valeurs multiples du champs associé.

---

## Structure des données retournées

Pour les graphiques, la requête doit retourner des colonnes correspondant aux axes :

| Type de module                     | Colonnes attendues                               |
|:-----------------------------------|:-------------------------------------------------|
| **Line, Bar, Pie, Doughnut, Maps** | 1 colonne as X (labels) + N colonnes Y (valeurs) |
| **Table**                          | Toutes les colonnes souhaitées                   |
| **Indicator**                      | 1 valeur as X                                    |
| **Gauge, Progress**                | 1 valeur numérique as X (pourcentage)            |

### Graphiques multi-séries avec la colonne Z

Pour créer des graphiques **multi-séries** dynamiques, vous pouvez utiliser une colonne aliasée **`as Z`**. Cette colonne définit le nom de chaque série.

| Alias | Rôle |
|:------|:-----|
| **X** | Labels de l'axe horizontal |
| **Y** | Valeurs de l'axe vertical |
| **Z** | Nom de la série (pour multi-séries) |

### Exemple multi-séries

Afficher les ventes mensuelles par année (chaque année devient une série) :

```sql
SELECT 
    YEAR(O.ORDERDATE) Z,  
    MONTH(O.ORDERDATE) X, 
    SUM(LINETOTAL) Y
FROM ORDERS O
GROUP BY MONTH(O.ORDERDATE), YEAR(O.ORDERDATE)
ORDER BY Z, X
```

{: .note }
> Dans cet exemple, chaque année (2023, 2024...) devient une série distincte sur le graphique, avec les mois en abscisse et le total des ventes en ordonnée.

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

