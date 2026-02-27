---
layout: default
title: Requêtes Builder
parent: Connecteurs
grand_parent: SYD Builder
nav_order: 2
---

# Requêtes Builder (Éditeur visuel)
{: .fs-8 }

Construction de requêtes SQL sans code
{: .fs-5 .fw-300 }

---

## Présentation

Le **Requêtes Builder** est un éditeur visuel permettant de construire des requêtes SQL sans écrire de code. Idéal pour les utilisateurs moins techniques ou pour créer rapidement des requêtes simples.

---

## Accéder au Builder

1. Dans le menu **Connecteurs**, cliquez sur **Requêtes Builder**
2. Cliquez sur **Nouveau** pour créer une nouvelle requête

---

## Interface

L'éditeur est organisé en onglets :

| Onglet | Description |
|:-------|:------------|
| **Données** | Sélection du connecteur, schéma et tables |
| **Colonnes** | Choix des colonnes à afficher |
| **GroupBy** | Regroupement des données |
| **Conditions** | Filtres WHERE |
| **Cond. Regroupement** | Filtres HAVING |
| **Order By** | Tri des résultats |

---

## Étape 1 : Données

### Connecteur

Sélectionnez la base de données source dans la liste déroulante **Sélectionner un Connecteur**.

### Schéma

Après sélection du connecteur, choisissez le schéma (si applicable).

### Tables

Sélectionnez les tables à utiliser. Vous pouvez sélectionner plusieurs tables pour les jointures.

### Label du jeu de données

Donnez un nom explicite à votre requête (ex: `Ventes par mois`).

---

## Étape 2 : Colonnes

Sélectionnez les colonnes à inclure dans le résultat.

### Ajouter une colonne

1. Dans le sélecteur de colonnes, choisissez une table
2. Sélectionnez la colonne souhaitée
3. La colonne s'ajoute à la liste

### Fonctions d'agrégation

Pour chaque colonne, vous pouvez appliquer une fonction :
- **COUNT** : Compter les occurrences
- **SUM** : Somme des valeurs
- **AVG** : Moyenne
- **MIN** : Valeur minimale
- **MAX** : Valeur maximale

### Alias

Renommez la colonne pour l'affichage avec un alias explicite.

---

## Étape 3 : GroupBy

Si vous utilisez des fonctions d'agrégation, définissez les colonnes de regroupement.

### Ajouter un groupement

1. Sélectionnez la colonne dans le sélecteur
2. Elle s'ajoute à la liste des colonnes de regroupement

### Exemple

Pour obtenir le total des ventes **par mois** et **par région** :
- GroupBy : `mois`, `region`
- Colonnes : `mois`, `region`, `SUM(montant)`

---

## Étape 4 : Conditions (WHERE)

Définissez les filtres à appliquer sur les données brutes.

### Ajouter une condition

1. Sélectionnez une colonne
2. Choisissez l'opérateur de comparaison
3. Saisissez la valeur

### Opérateurs disponibles

| Opérateur | Description | Exemple |
|:----------|:------------|:--------|
| `=` | Égal | `status = 'actif'` |
| `!=` | Différent | `status != 'supprimé'` |
| `>` | Supérieur | `montant > 1000` |
| `<` | Inférieur | `quantite < 10` |
| `>=` | Supérieur ou égal | `date >= '2024-01-01'` |
| `<=` | Inférieur ou égal | `date <= '2024-12-31'` |
| `LIKE` | Contient | `nom LIKE '%dupont%'` |
| `IN` | Dans une liste | `region IN ('Nord', 'Sud')` |
| `IS NULL` | Est vide | `email IS NULL` |
| `IS NOT NULL` | N'est pas vide | `telephone IS NOT NULL` |

### Conditions multiples

Ajoutez plusieurs conditions. Elles seront combinées avec **AND** (toutes doivent être vraies).

---

## Étape 5 : Conditions de regroupement (HAVING)

Filtrez les résultats **après** le regroupement.

### Différence avec WHERE

- **WHERE** : Filtre les lignes avant le regroupement
- **HAVING** : Filtre les groupes après le regroupement

### Exemple

Pour afficher uniquement les régions avec plus de 10 000 € de ventes :
```
HAVING SUM(montant) > 10000
```

---

## Étape 6 : Order By

Définissez l'ordre de tri des résultats.

### Ajouter un tri

1. Sélectionnez la colonne
2. Choisissez l'ordre : **ASC** (croissant) ou **DESC** (décroissant)

### Tri multiple

Vous pouvez définir plusieurs niveaux de tri. Le premier critère est prioritaire.

---

## Valider et tester

1. Cliquez sur **Valider** pour enregistrer la requête
2. La requête SQL générée est stockée automatiquement
3. Utilisez-la dans vos modules comme une requête classique

---

## Limitations

{: .note }
> Le Builder ne supporte pas toutes les fonctionnalités SQL avancées.

Pour des requêtes complexes nécessitant :
- Jointures complexes (OUTER JOIN, CROSS JOIN)
- Sous-requêtes
- UNION
- Fonctions SQL spécifiques

→ Utilisez l'éditeur de [Requêtes SQL]({{ site.baseurl }}/builder/connecteurs/requetes/) classique.

---

## Bonnes pratiques

- **Nommez explicitement** vos colonnes avec des alias
- **Testez** votre requête avant de l'utiliser dans un module
- **Limitez** le nombre de colonnes pour de meilleures performances
- **Utilisez les index** : filtrez sur des colonnes indexées

