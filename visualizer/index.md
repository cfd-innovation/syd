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

![Dashboard Visualizer]({{ site.baseurl }}/assets/img/visualizer/Mire_connexion_Visualizer.png)

---

## Interface principale

L'interface du Visualizer se compose de :

### 1. Barre de navigation

- **Logo** : Retour à l'accueil
- **Menu des dashboards** : Accès aux tableaux de bord disponibles organisés par Catégories
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

![Module 1 Visualizer]({{ site.baseurl }}/assets/img/visualizer/Module_SYD_Visualizer.png)
![Module 2 Visualizer]({{ site.baseurl }}/assets/img/visualizer/Module_SYD_Visualizer_2.png)

---

## Navigation

### Accéder à un dashboard

1. Cliquez sur le **menu des dashboards** dans la barre de navigation
2. Les dashboards sont organisés par **catégories**
3. Cliquez sur le dashboard souhaité

![Menu Visualizer]({{ site.baseurl }}/assets/img/visualizer/Menu_Visualizer.png)


### Dashboards favoris

Selon la configuration côté builder, vous pouvez avoir un dashboard par défaut qui s'affiche à la connexion.

---

## Interaction avec les modules

### Survol (Tooltip)

Passez la souris sur un élément du graphique pour afficher les détails :
- Valeur précise
- Libellé de la série
- Informations complémentaires

![Tooltip Visualizer]({{ site.baseurl }}/assets/img/visualizer/Tooltip_visualizer.png)

### Légende interactive

Cliquez sur les éléments de la légende pour :
- **Masquer** une série (clic simple)
- **Afficher** une série masquée (clic à nouveau)

![Légendes Visualizer]({{ site.baseurl }}/assets/img/visualizer/Legendes_visualizer.png)

### Zoom (certains graphiques)

Pour les graphiques supportant le zoom (maps) :
- **Molette** : Zoom avant/arrière
- **Clic glissé** : Sélection d'une zone

### Zoom module (plein écran)

Si l'option a été activée dans le Builder sur le module, une icône **loupe** apparaît dans sa barre d'outils.

- **Clic sur la loupe** : le module passe en affichage agrandi sur toute la page
- **Clic à nouveau** : retour à l'affichage normal du dashboard

---

## Formulaires de filtres

Si le dashboard dispose d'un formulaire de filtrage :

1. Les champs de filtre s'affichent en haut du dashboard
2. Sélectionnez vos critères de filtrage
3. Cliquez sur **Appliquer** (ou le bouton d'action)
4. Les modules se rafraîchissent avec les données filtrées

![Filtres Visualizer]({{ site.baseurl }}/assets/img/visualizer/Filtres_visualizer.png)

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
> L'export prend en compte les filtres actifs. Les données exportées correspondent soit à la sélection en cours soit à une requête spécifique définie dans le builder.

---

## Rafraîchissement

### Rafraîchissement automatique

Certains modules sont configurés pour se rafraîchir automatiquement à intervalle régulier. Les données sont mises à jour sans intervention de l'utilisateur.

### Rafraîchissement manuel

Si le module dispose d'un bouton de rafraîchissement :

1. Cliquez sur l'icône **Refresh** 
2. Les données du module sont rechargées

---
