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
2. Cliquez sur **Nouveau** 

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

1. Dans le menu **Formulaires**, cliquez sur **Gestion des champs de formulaire**
2. Cliquez sur **Nouveau**

### Configuration commune

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Nom du champ** | Identifiant technique (utilisé dans les requêtes) | `date_debut` |
| **Label** | Libellé affiché à l'utilisateur | `Date de début` |
| **Type** | Type de champ | `Input`, `Select`, `Select Dynamic` |

---

## Utilisation dans les requêtes

Les valeurs des champs de formulaire sont injectées dans les requêtes SQL des modules via des **paramètres**. La syntaxe dépend du type de champ (valeur unique ou valeurs multiples).

### Syntaxe pour valeur unique

Pour les champs **Input** ou **Select** sans sélection multiple :

```sql
###nom_du_champ###
```

**Exemple :**
```sql
SELECT * FROM table WHERE attribut = ###nom_param###
```

### Syntaxe pour valeurs multiples

Pour les champs **Select** ou **Select Dynamic** avec sélection multiple activée :

```sql
&&&nom_du_champ&&&
```

**Exemple :**
```sql
SELECT * FROM table WHERE attribut IN (&&&nom_param&&&)
```

{: .warning }
> Les deux types de paramètres (`###` et `&&&`) **ne peuvent pas être utilisés dans la même requête**.

### Exemple complet

**Champs de formulaire :**
- `annee` (Select - valeur unique)
- `regions` (Select Dynamic - valeurs multiples)

**Requête SQL du module (valeur unique) :**
```sql
SELECT mois, SUM(montant) as total
FROM ventes
WHERE annee = ###annee###
GROUP BY mois
```

**Requête SQL du module (valeurs multiples) :**
```sql
SELECT region, SUM(montant) as total
FROM ventes
WHERE region IN (&&&regions&&&)
GROUP BY region
```

{: .important }
> Le nom du paramètre dans la requête doit correspondre exactement au **Nom du champ** défini dans le formulaire.

---

## Associer un formulaire à un dashboard

1. Modifiez le dashboard concerné
2. Dans le champ **Formulaire**, sélectionnez le formulaire créé
3. Validez

Le formulaire apparaîtra en haut du dashboard dans le Visualizer.

---

## Formulaires chaînés

Les **formulaires chaînés** permettent de créer une dépendance entre deux listes déroulantes : la sélection dans un premier champ filtre dynamiquement les options disponibles dans un second champ.

### Cas d'utilisation

- **Région → Département** : Sélectionner une région filtre la liste des départements
- **Catégorie → Produit** : Sélectionner une catégorie filtre la liste des produits
- **Année → Mois** : Sélectionner une année filtre les mois disponibles

### Configuration

Le chaînage est configuré sur le **champ enfant** (celui qui dépend de l'autre).

#### Étape 1 : Créer le champ parent

Créez un champ de type **Select** ou **Select Dynamic** qui servira de filtre principal.

**Exemple** : Champ `region` (Select Dynamic)
```sql
SELECT DISTINCT region AS label, region AS value FROM zones
```

#### Étape 2 : Créer le champ enfant chaîné

1. Créez un nouveau champ de type **Select Dynamic**
2. Cochez l'option **Champ de formulaire chaîné**
3. Dans **Champ de formulaire à lier**, sélectionnez le champ parent (`region`)
4. Rédigez la requête en utilisant la syntaxe de paramètre spéciale

### Syntaxe des paramètres chaînés

{: .important }
> Dans les requêtes de champs chaînés, le paramètre est toujours nommé **`value`** (et non le nom du champ parent).

#### Pour un champ parent à valeur unique

```sql
###value###
```

**Exemple** : Champ `departement` chaîné à `region`
```sql
SELECT DISTINCT departement AS label, departement AS value 
FROM zones 
WHERE region = ###value###
```

#### Pour un champ parent à valeurs multiples

```sql
&&&value&&&
```

**Exemple** : Champ `departement` chaîné à `region` (multiple)
```sql
SELECT DISTINCT departement AS label, departement AS value 
FROM zones 
WHERE region IN (&&&value&&&)
```

{: .warning }
> Les deux types de paramètres (`###value###` et `&&&value&&&`) ne peuvent pas être utilisés dans la même requête.

### Exemple complet : Région → Département

#### 1. Champ parent : `region`

| Configuration | Valeur |
|:--------------|:-------|
| Nom du champ | `region` |
| Label | `Région` |
| Type | Select Dynamic |
| Connecteur BDD | (votre connecteur) |
| Requête | `SELECT DISTINCT region AS label, region AS value FROM zones` |

#### 2. Champ enfant : `departement`

| Configuration | Valeur |
|:--------------|:-------|
| Nom du champ | `departement` |
| Label | `Département` |
| Type | Select Dynamic |
| Connecteur BDD | (votre connecteur) |
| Requête | `SELECT DISTINCT departement AS label, departement AS value FROM zones WHERE region = ###value###` |
| Champ de formulaire chaîné | ✅ Coché |
| Champ de formulaire à lier | `region` |

#### 3. Comportement dans le Visualizer

1. L'utilisateur sélectionne une région (ex: "Île-de-France")
2. La liste des départements se met à jour automatiquement pour n'afficher que ceux de la région sélectionnée (75, 77, 78, 91, 92, 93, 94, 95)
3. L'utilisateur peut alors sélectionner un département parmi ceux filtrés

### Bonnes pratiques pour les champs chaînés

- **Ordre dans le formulaire** : Placez le champ parent avant le champ enfant
- **Valeur par défaut** : Configurez une valeur par défaut sur le champ parent pour que le champ enfant soit alimenté dès le chargement
- **Performance** : Indexez les colonnes utilisées pour le filtrage dans vos tables

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

