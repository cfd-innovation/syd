---
layout: default
title: SYD Visualizer
nav_order: 3
has_children: true
permalink: /visualizer/
---

# SYD Visualizer
{: .fs-9 }

Interface de consultation des tableaux de bord
{: .fs-6 .fw-300 }

---

## Présentation

**SYD Visualizer** est l'interface destinée aux utilisateurs finaux. Elle permet de :

- **Consulter** les dashboards autorisés
- **Interagir** avec les modules (filtres, drill-down)
- **Exporter** les données au format Excel
- **Naviguer** entre les différents tableaux de bord

---

## Accès au Visualizer

### Connexion

1. Accédez à l'URL du Visualizer fournie par votre administrateur
2. Saisissez vos identifiants de connexion
3. Cliquez sur **Se connecter**

{: .note }
> Certains dashboards peuvent être configurés en mode **public** et accessibles sans authentification.

---

## Interface principale

L'interface du Visualizer se compose de :

### 1. Barre de navigation

- **Logo** : Retour à l'accueil
- **Menu des dashboards** : Accès aux tableaux de bord disponibles
- **Catégories** : Dashboards regroupés par thème
- **Utilisateur** : Informations de connexion et déconnexion

### 2. Zone de contenu

- **Titre du dashboard** : Nom et sous-titre du tableau de bord actif
- **Formulaire de filtres** : Champs de sélection (si configuré)
- **Modules** : Visualisations disposées selon le layout défini

### 3. Modules

Chaque module affiche :
- **Titre** : Nom du module
- **Visualisation** : Graphique, tableau, indicateur...
- **Barre d'outils** : Actions disponibles (refresh, export...)

---

## Navigation

### Accéder à un dashboard

1. Cliquez sur le **menu des dashboards** dans la barre de navigation
2. Les dashboards sont organisés par **catégories**
3. Cliquez sur le dashboard souhaité

### Dashboards favoris

Selon la configuration, vous pouvez avoir un dashboard par défaut qui s'affiche à la connexion.

---

## Interaction avec les modules

### Survol (Tooltip)

Passez la souris sur un élément du graphique pour afficher les détails :
- Valeur précise
- Libellé de la série
- Informations complémentaires

### Légende interactive

Cliquez sur les éléments de la légende pour :
- **Masquer** une série (clic simple)
- **Afficher** une série masquée (clic à nouveau)

### Zoom (certains graphiques)

Pour les graphiques supportant le zoom :
- **Molette** : Zoom avant/arrière
- **Clic glissé** : Sélection d'une zone

---

## Formulaires de filtres

Si le dashboard dispose d'un formulaire de filtrage :

1. Les champs de filtre s'affichent en haut du dashboard
2. Sélectionnez vos critères de filtrage
3. Cliquez sur **Appliquer** (ou le bouton d'action)
4. Les modules se rafraîchissent avec les données filtrées

### Types de filtres

| Type | Usage |
|:-----|:------|
| **Champ texte** | Saisie libre (recherche, date...) |
| **Liste déroulante** | Sélection parmi des options |
| **Multi-sélection** | Choix de plusieurs valeurs |

---

## Export des données

### Export Excel

Pour les modules avec export activé :

1. Repérez l'**icône Excel** dans la barre d'outils du module
2. Cliquez sur l'icône
3. Le fichier `.xlsx` se télécharge automatiquement

{: .note }
> L'export prend en compte les filtres actifs. Les données exportées correspondent à la sélection en cours.

---

## Rafraîchissement

### Rafraîchissement automatique

Certains modules sont configurés pour se rafraîchir automatiquement à intervalle régulier. Un indicateur peut signaler le prochain rafraîchissement.

### Rafraîchissement manuel

Si le module dispose d'un bouton de rafraîchissement :

1. Cliquez sur l'icône **Refresh** 
2. Les données du module sont rechargées

---

## Voir aussi

- [Authentification]({{ site.baseurl }}/visualizer/authentification/)
- [Types de modules]({{ site.baseurl }}/builder/modules/)

