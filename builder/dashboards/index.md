---
layout: default
title: Dashboards
parent: SYD Builder
nav_order: 3
has_children: true
permalink: /builder/dashboards/
---

# Dashboards
{: .fs-8 }

Création et gestion des tableaux de bord
{: .fs-5 .fw-300 }

---

## Présentation

Un **Dashboard** (tableau de bord) est un regroupement de modules affichés sur une même page. Il constitue l'élément principal que les utilisateurs finaux consultent dans le Visualizer.

---

## Créer un dashboard

### Étape 1 : Accéder au formulaire

1. Dans le menu, cliquez sur **Dashboards**
2. Cliquez sur **Nouveau** (ou **+**)

### Étape 2 : Configuration générale

<!-- ![Formulaire dashboard]({{ site.baseurl }}/assets/img/builder/dashboard-form.png) -->

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Titre** | Nom du dashboard | `Ventes 2024` |
| **Sous-titre** | Description secondaire | `Suivi mensuel des ventes` |
| **Dark mode** | Appliquer un fond sombre | ☑️ / ☐ |
| **Couleur de fond** | Couleur personnalisée | `#FFFFFF` |
| **Utilisateurs** | Utilisateurs autorisés | Multi-sélection |
| **Modules** | Modules à inclure | Multi-sélection |
| **Catégorie** | Catégorie de classement | `NO_CATEGORY` ou catégorie |
| **Formulaire** | Formulaire de filtrage | `NO_FORM` ou formulaire |
| **Public** | Accessible sans authentification | ☑️ / ☐ |

### Étape 3 : Valider

Cliquez sur **Valider** pour créer le dashboard.

---

## Configuration détaillée

### Attribution des utilisateurs

Sélectionnez les utilisateurs qui auront accès à ce dashboard. Utilisez la recherche pour trouver rapidement un utilisateur.

{: .note }
> Si aucun utilisateur n'est sélectionné et que le dashboard n'est pas public, personne ne pourra y accéder.

### Sélection des modules

Choisissez les modules à afficher sur le dashboard. L'ordre et le positionnement seront configurés dans l'écran de **Layout**.

### Catégorie

Les catégories permettent d'organiser vos dashboards par thèmes. Sélectionnez :
- **NO_CATEGORY** : Pas de catégorie (dashboard non classé)
- Une catégorie existante : Voir [Gestion des catégories]({{ site.baseurl }}/builder/categories/)

### Formulaire

Associez un formulaire de filtrage au dashboard :
- **NO_FORM** : Pas de formulaire
- Un formulaire existant : Les filtres seront affichés et appliqueront leurs valeurs aux modules

### Dashboard public

{: .warning }
> Un dashboard public est accessible sans authentification. Utilisez cette option avec précaution.

Cochez **Public** pour rendre le dashboard accessible à tous, sans connexion requise.

---

## Dark mode et couleur de fond

### Dark mode

Active un thème sombre pour le dashboard entier :
- Fond sombre
- Textes clairs
- Meilleur confort visuel en conditions de faible luminosité

### Couleur de fond personnalisée

Définissez une couleur de fond spécifique grâce au sélecteur de couleur. Par défaut : blanc (`#FFFFFF`).

---

## Après la création

Une fois le dashboard créé, vous pouvez :

1. **Configurer le Layout** : Positionner et redimensionner les modules
2. **Gérer les utilisateurs** : Modifier les accès
3. **Prévisualiser** : Voir le résultat dans le Visualizer

---

## Voir aussi

- [Layout des modules]({{ site.baseurl }}/builder/dashboards/layout/)
- [Gestion des utilisateurs]({{ site.baseurl }}/builder/dashboards/utilisateurs/)
- [Catégories]({{ site.baseurl }}/builder/categories/)
- [Formulaires]({{ site.baseurl }}/builder/formulaires/)

