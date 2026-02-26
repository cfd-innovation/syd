---
layout: default
title: Formulaires
parent: SYD Builder
nav_order: 4
has_children: true
permalink: /builder/formulaires/
---

# Formulaires
{: .fs-8 }

Création de formulaires de filtrage pour les dashboards
{: .fs-5 .fw-300 }

---

## Présentation

Les **formulaires** permettent de créer des filtres interactifs pour les dashboards. Les utilisateurs peuvent ainsi ajuster les données affichées selon leurs critères.

Un formulaire est composé de **champs de formulaire** (fields) qui peuvent être de différents types : saisie libre, liste déroulante, liste dynamique...

---

## Architecture

```
Formulaire
├── Champ 1 (Input)
├── Champ 2 (Select)
├── Champ 3 (Select Dynamic)
└── ...
```

1. **Créer les champs** : Définir les champs individuels
2. **Créer le formulaire** : Assembler les champs dans un formulaire
3. **Associer au dashboard** : Lier le formulaire à un ou plusieurs dashboards

---

## Créer un formulaire

### Étape 1 : Accéder au formulaire

1. Dans le menu, cliquez sur **Formulaires**
2. Cliquez sur **Nouveau** (ou **+**)

### Étape 2 : Configuration

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Nom du formulaire** | Identifiant du formulaire | `Filtres ventes` |
| **Champs de formulaire** | Champs à inclure | Multi-sélection |

### Étape 3 : Valider

Cliquez sur **Valider** pour créer le formulaire.

---

## Types de champs

### Input (Saisie libre)

Champ de saisie texte libre.

| Configuration | Description |
|:--------------|:------------|
| **Placeholder** | Texte d'indication grisé |
| **Valeur par défaut** | Valeur pré-remplie |

**Cas d'usage** : Recherche par mot-clé, saisie de code, date libre...

### Select (Liste déroulante statique)

Liste de choix prédéfinis.

| Configuration | Description |
|:--------------|:------------|
| **Valeurs & Labels** | Couples valeur/libellé à afficher |
| **Multiple** | Autoriser la sélection multiple |
| **Valeur par défaut** | `Premier`, `Dernier`, `Tous`, `Aucun` |

**Cas d'usage** : Choix de région, statut, catégorie fixe...

### Select Dynamic (Liste dynamique)

Liste alimentée par une requête SQL.

| Configuration | Description |
|:--------------|:------------|
| **Connecteur BDD** | Base de données source |
| **Requête** | SQL pour récupérer les valeurs |
| **Multiple** | Autoriser la sélection multiple |
| **Valeur par défaut** | `Premier`, `Dernier`, `Tous`, `Aucun` |

**Cas d'usage** : Liste de clients, produits, années disponibles...

---

## Créer un champ de formulaire

### Accès

1. Dans le menu **Formulaires**, cliquez sur **Champs**
2. Cliquez sur **Nouveau**

### Configuration commune

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Nom du champ** | Identifiant technique (utilisé dans les requêtes) | `date_debut` |
| **Label** | Libellé affiché à l'utilisateur | `Date de début` |
| **Type** | Type de champ | `Input`, `Select`, `Select Dynamic` |

---

## Utilisation dans les requêtes

Les valeurs des champs de formulaire sont injectées dans les requêtes SQL via des **paramètres**.

### Syntaxe

```sql
WHERE colonne = '{{nom_du_champ}}'
```

### Exemple complet

**Champs de formulaire :**
- `date_debut` (Input)
- `date_fin` (Input)
- `region` (Select)

**Requête SQL du module :**
```sql
SELECT mois, SUM(montant) as total
FROM ventes
WHERE date_vente BETWEEN '{{date_debut}}' AND '{{date_fin}}'
  AND region = '{{region}}'
GROUP BY mois
```

{: .important }
> Le nom du champ dans la requête (`{{nom_du_champ}}`) doit correspondre exactement au **Nom du champ** défini dans le formulaire.

---

## Associer un formulaire à un dashboard

1. Modifiez le dashboard concerné
2. Dans le champ **Formulaire**, sélectionnez le formulaire créé
3. Validez

Le formulaire apparaîtra en haut du dashboard dans le Visualizer.

---

## Bonnes pratiques

### Nommage des champs

- Utilisez des noms techniques sans espaces ni caractères spéciaux
- Exemples : `date_debut`, `region`, `client_id`, `annee`

### Valeurs par défaut

- **Select** : Définissez une valeur par défaut pertinente pour éviter les résultats vides
- **Input** : Pré-remplissez si une valeur est souvent utilisée

### Performance

- **Select Dynamic** : Limitez le nombre de valeurs retournées
- Indexez les colonnes utilisées dans les filtres

---

## Voir aussi

- [Requêtes SQL]({{ site.baseurl }}/builder/connecteurs/requetes/)
- [Dashboards]({{ site.baseurl }}/builder/dashboards/)

