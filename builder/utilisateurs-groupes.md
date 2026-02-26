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

