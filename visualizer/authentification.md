---
layout: default
title: Authentification
parent: SYD Visualizer
nav_order: 1
---

# Authentification
{: .fs-8 }

Connexion et gestion des sessions utilisateur
{: .fs-5 .fw-300 }

---

## Page de connexion

Pour accéder au Visualizer, vous devez vous authentifier via la page de connexion.

<!-- ![Page de connexion]({{ site.baseurl }}/assets/img/visualizer/login.png) -->

### Champs de connexion

| Champ | Description |
|:------|:------------|
| **Utilisateur** | Votre identifiant de connexion |
| **Mot de passe** | Votre mot de passe |

### Étapes

1. Saisissez votre **nom d'utilisateur**
2. Saisissez votre **mot de passe**
3. Cliquez sur **Se connecter**

---

## Langue de l'interface

Le Visualizer supporte plusieurs langues :

| Langue | Code |
|:-------|:-----|
| **Français** | fr_FR |
| **Anglais** | en_US |
| **Italien** | it_IT |

### Changer la langue

1. Sur la page de connexion, utilisez le **sélecteur de langue** en haut
2. Sélectionnez la langue souhaitée
3. L'interface s'adapte immédiatement

{: .note }
> Le choix de la langue est conservé dans un cookie et mémorisé pour vos prochaines visites.

---

## Dashboards publics

Certains dashboards peuvent être configurés en mode **public** par l'administrateur. Ces dashboards sont accessibles sans authentification via une URL directe.

{: .warning }
> Les dashboards publics sont visibles par tous. Ils ne doivent contenir que des données non sensibles.

---

## Déconnexion

Pour vous déconnecter :

1. Cliquez sur votre **nom d'utilisateur** dans la barre de navigation
2. Sélectionnez **Déconnexion**
3. Vous êtes redirigé vers la page de connexion

---

## Erreurs de connexion

### Messages d'erreur courants

| Message | Cause | Solution |
|:--------|:------|:---------|
| Identifiants incorrects | Mauvais login/mot de passe | Vérifiez vos identifiants |
| Compte désactivé | Compte supprimé ou désactivé | Contactez l'administrateur |
| Accès refusé | Pas de droits sur les dashboards | Contactez l'administrateur |

### En cas de problème

1. Vérifiez que le **Caps Lock** n'est pas activé
2. Assurez-vous d'utiliser les bons identifiants
3. Contactez votre administrateur SYD si le problème persiste

---

## Sécurité

### Bonnes pratiques

- **Ne partagez pas** vos identifiants
- **Déconnectez-vous** après utilisation sur un poste partagé
- **Signalez** toute activité suspecte à l'administrateur

### Session

Votre session reste active tant que :
- Vous n'êtes pas déconnecté manuellement
- Le délai d'expiration n'est pas atteint (configurable par l'administrateur)
- Vous n'avez pas fermé votre navigateur (selon la configuration)

