---
layout: default
title: Utilisateurs et Groupes
parent: SYD Builder
nav_order: 5
permalink: /builder/utilisateurs-groupes/
---

# Utilisateurs et Groupes
{: .fs-8 }

Gestion des accès aux dashboards
{: .fs-5 .fw-300 }

---

## Présentation

SYD propose deux niveaux de gestion des accès :
- **Utilisateurs** : Comptes individuels pouvant se connecter
- **Groupes** : Regroupements d'utilisateurs partageant les mêmes droits

---

## Utilisateurs

### Créer un utilisateur

1. Dans le menu, cliquez sur **Utilisateurs**
2. Cliquez sur **Nouveau**

### Configuration

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Utilisateur** | Nom d'utilisateur (login) | `jdupont` |
| **Label** | Nom affiché | `Jean Dupont` |
| **Droit Administrateur** | Accès à l'interface Builder | ☑️ / ☐ |

### Types d'utilisateurs

| Type | Accès Builder | Accès Visualizer |
|:-----|:--------------|:-----------------|
| **Standard** | ❌ | ✅ (dashboards autorisés) |
| **Administrateur** | ✅ | ✅ (tous les dashboards) |

{: .warning }
> Les utilisateurs administrateurs ont accès à toutes les fonctionnalités du Builder et peuvent voir tous les dashboards.

### Ordre d'affichage des dashboards

Pour chaque utilisateur, il est possible de définir l'**ordre d'affichage des dashboards** dans le Visualizer. Cet ordre détermine l'organisation du menu de navigation pour l'utilisateur.

#### Accéder à la configuration

1. Dans la liste des utilisateurs, cliquez sur le bouton **Layout** de l'utilisateur concerné
2. La fenêtre "Formulaire Layout du user" s'ouvre

#### Fonctionnalités disponibles

| Action | Description |
|:-------|:------------|
| **Réorganiser** | Glissez-déposez les dashboards pour modifier leur ordre |
| **Ajouter** | Sélectionnez un dashboard dans la liste déroulante et cliquez sur **+** |
| **Supprimer** | Cliquez sur le bouton de suppression (❌) à côté du dashboard |

{: .note }
> Les dashboards attribués via un **groupe** ne peuvent pas être supprimés individuellement depuis cette interface (bouton désactivé). Pour les retirer, il faut modifier l'appartenance au groupe.

#### Cas d'utilisation

- **Prioriser** les dashboards les plus utilisés en les plaçant en haut de la liste
- **Personnaliser** l'expérience utilisateur en fonction de son rôle
- **Ajouter** des dashboards spécifiques à un utilisateur sans passer par les groupes

---

## Groupes

Les groupes permettent de gérer les accès de manière collective.

### Créer un groupe

1. Dans le menu, cliquez sur **Groupes**
2. Cliquez sur **Nouveau**

### Configuration

| Champ | Description |
|:------|:------------|
| **Nom du groupe** | Identifiant du groupe |
| **Utilisateurs membres** | Utilisateurs appartenant au groupe |
| **Droits d'accès** | Dashboards accessibles au groupe |

### Fonctionnement

- Un utilisateur peut appartenir à **plusieurs groupes**
- Un utilisateur a accès à **tous les dashboards de ses groupes**
- Les accès sont **cumulatifs** : accès directs + accès via groupes

---

## Attribution des accès

### Méthode 1 : Via le dashboard

Lors de la création/modification d'un dashboard :
1. Sélectionnez les utilisateurs autorisés dans le champ **Utilisateurs**
2. Validez

### Méthode 2 : Via les groupes

1. Créez un groupe avec les utilisateurs concernés
2. Attribuez les dashboards au groupe

### Comparaison

| Méthode | Avantages | Inconvénients |
|:--------|:----------|:--------------|
| **Directe** | Simple, rapide | Gestion individuelle |
| **Groupes** | Gestion centralisée, scalable | Configuration initiale |

---

## Exemple d'organisation

### Structure typique

```
Groupe "Direction"
├── Utilisateur: directeur
├── Utilisateur: directrice_adjointe
└── Dashboards: CA Global, KPIs Direction

Groupe "Commercial"
├── Utilisateur: commercial1
├── Utilisateur: commercial2
├── Utilisateur: commercial3
└── Dashboards: Ventes par région, Pipeline commercial

Groupe "Production"
├── Utilisateur: responsable_prod
├── Utilisateur: technicien1
└── Dashboards: Suivi production, Qualité
```

### Utilisateur multi-groupes

Un directeur commercial pourrait appartenir à :
- Groupe "Direction" → accès aux dashboards direction
- Groupe "Commercial" → accès aux dashboards commerciaux

---

## Authentification

### Mode standard

Les utilisateurs se connectent avec leur identifiant configuré dans SYD.

{: .note }
> Le mot de passe peut être géré via une authentification externe (LDAP, SSO) selon la configuration.

### Authentification IBM i (DB2 for i)

Lorsque la base de données système de SYD est **DB2 for i**, l'authentification fonctionne de manière intégrée avec l'IBM i :

| Élément SYD | Correspondance IBM i |
|:------------|:---------------------|
| **Utilisateur SYD** | Profil utilisateur IBM i (USRPRF) |
| **Mot de passe** | Mot de passe du profil IBM i |

#### Fonctionnement

- Les **utilisateurs SYD** représentent les **profils IBM i (USRPRF)** autorisés à accéder à l'application
- La **vérification du couple profil/mot de passe** est gérée directement par l'IBM i
- **Aucun mot de passe supplémentaire** n'est à gérer dans SYD : l'authentification est déléguée à l'IBM i

{: .important }
> Dans ce mode, créer un utilisateur dans SYD revient à **autoriser un profil IBM i existant** à utiliser l'application. Le nom d'utilisateur saisi doit correspondre exactement au nom du profil IBM i (USRPRF).

#### Avantages

- **Authentification centralisée** : les utilisateurs utilisent leurs identifiants IBM i habituels
- **Sécurité renforcée** : la gestion des mots de passe est assurée par l'IBM i (règles de complexité, expiration, etc.)
- **Simplification** : pas de double gestion des mots de passe

### Dashboards publics

Les dashboards marqués comme **Public** sont accessibles sans authentification.

---

## Bonnes pratiques

### Organisation des groupes

- **Par service** : Commercial, Marketing, Production, Direction
- **Par projet** : Projet A, Projet B
- **Par niveau d'accès** : Managers, Opérateurs, Invités

### Nommage des utilisateurs

- Utilisez des identifiants cohérents (prénom.nom, initiales...)
- Remplissez le label pour faciliter l'identification

### Sécurité

- Limitez le nombre d'administrateurs
- Revoyez régulièrement les accès
- Supprimez les utilisateurs inactifs

