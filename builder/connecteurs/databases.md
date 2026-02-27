---
layout: default
title: Bases de données
parent: Connecteurs
grand_parent: SYD Builder
nav_order: 1
---

# Bases de données
{: .fs-8 }

Configuration des connexions aux bases de données
{: .fs-5 .fw-300 }

---

## Présentation

Les connecteurs de base de données permettent d'établir des connexions directes vers différents systèmes de gestion de bases de données (SGBD). Ces connexions seront utilisées par les requêtes SQL pour extraire les données.

## Drivers supportés

| Driver | Description | Usage |
|:-------|:------------|:------|
| **mysql** | Driver natif MySQL | Bases MySQL/MariaDB |
| **db2** | Driver IBM DB2 | Bases DB2, AS/400, IBMi |
| **pdo** | PHP Data Objects | Connexions génériques |

## SGBD supportés

| SGBD | Description |
|:-----|:------------|
| **mysql** | MySQL / MariaDB |
| **db2** | IBM DB2 |
| **sqlsrv** | Microsoft SQL Server |
| **dblib** | SQL Server via DBLib (IBMi) |

---

## Créer un connecteur de base de données

### Étape 1 : Accéder au formulaire

1. Dans le menu **Connecteurs**, sélectionnez **Bases de données**
2. Cliquez sur le bouton **Nouveau** (ou **+**)

### Étape 2 : Remplir le formulaire

<!-- ![Formulaire base de données]({{ site.baseurl }}/assets/img/builder/database-form.png) -->

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Type** | Driver de connexion | `mysql`, `db2`, `pdo` |
| **SGBD** | Type de système de gestion | `mysql`, `db2`, `sqlsrv` |
| **Label** | Nom de la connexion (pour identification) | `Production MySQL` |
| **Host** | Adresse du serveur | `192.168.1.100` ou `localhost` |
| **Profil** | Nom d'utilisateur de connexion | `admin` |
| **Mot de passe** | Mot de passe de connexion | `********` |
| **DB Name** | Nom de la base de données | `ma_base` |

### Étape 3 : Valider

Cliquez sur **Valider** pour enregistrer la connexion.

---

## Configuration PDO

{: .note }
> Lors de l'utilisation du driver **PDO**, un bouton d'aide affiche les chaînes de connexion disponibles.

### Chaînes de connexion PDO

**Pour DB2 / IBMi :**
```
odbc:DRIVER={IBM i Access ODBC Driver};SYSTEM=host;CCSID=1208;DEBUG=524288;DBQ=dbname;NAM=1
```

**Pour MySQL :**
```
mysql:host=servername;dbname=myDB
```

---

## Bonnes pratiques

{: .important }
> **Sécurité** : Utilisez des comptes de base de données avec des droits limités en lecture seule lorsque c'est possible.

- **Nommage** : Utilisez des labels explicites pour identifier facilement vos connexions
- **Documentation** : Notez les informations de connexion dans un document sécurisé

---

## Tester une connexion

Un bouton **Test** est disponible pour vérifier la connexion à la base de données.

### Procédure

1. Dans la liste des connecteurs, repérez la connexion à tester
2. Cliquez sur le bouton **Test**
3. Le résultat s'affiche dans la colonne **État**

### Résultats possibles

| État | Affichage | Signification |
|:-----|:----------|:--------------|
| ✅ Succès | Bouton vert **Connecté** | La connexion à la base de données fonctionne |
| ❌ Échec | Bouton rouge **Echec** | La connexion a échoué (vérifiez les paramètres) |

{: .note }
> En cas d'échec, vérifiez les paramètres de connexion (host, identifiants, nom de la base) et consultez la section Dépannage ci-dessous.

---

## Dépannage

| Problème | Solution possible |
|:---------|:------------------|
| Connexion refusée | Vérifiez l'adresse IP/hostname et le port |
| Accès refusé | Vérifiez les identifiants et les droits utilisateur |
| Base introuvable | Vérifiez le nom de la base de données |
| Driver non trouvé | Vérifiez l'installation des extensions PHP requises |

