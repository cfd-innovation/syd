---
layout: default
title: Webservices
parent: Connecteurs
grand_parent: SYD Builder
nav_order: 2
---

# Webservices
{: .fs-8 }

Configuration des appels à des APIs REST
{: .fs-5 .fw-300 }

---

## Présentation

Les connecteurs **Webservice** permettent d'appeler des APIs REST externes pour récupérer des données. Ces données peuvent ensuite être utilisées comme source pour vos modules.

---

## Créer un connecteur Webservice

### Étape 1 : Accéder au formulaire

1. Dans le menu **Connecteurs**, sélectionnez **Webservices**
2. Cliquez sur le bouton **Nouveau** (ou **+**)

### Étape 2 : Remplir le formulaire

<!-- ![Formulaire webservice]({{ site.baseurl }}/assets/img/builder/webservice-form.png) -->

| Champ | Description | Exemple |
|:------|:------------|:--------|
| **Méthode** | Méthode HTTP | `GET`, `POST`, `PUT`, `DELETE` |
| **URL** | Adresse de l'API | `https://api.example.com/data` |
| **Type d'authentification** | Mode d'authentification | Voir ci-dessous |
| **Auth** | Identifiants d'authentification | Voir ci-dessous |
| **Paramètres** | Corps de la requête (JSON) | `{"limit": 100}` |
| **Chemin d'accès X** | Attribut pour l'axe X | `date` |
| **Chemin d'accès Y** | Attribut pour l'axe Y | `value` |
| **Vérification des certificats** | SSL/TLS | Activer/Désactiver |

---

## Méthodes HTTP

| Méthode | Usage typique |
|:--------|:--------------|
| **GET** | Récupérer des données (lecture) |
| **POST** | Envoyer des données (création) |
| **PUT** | Mettre à jour des données |
| **DELETE** | Supprimer des données |

{: .note }
> Pour la plupart des cas d'affichage de données, vous utiliserez la méthode **GET**.

---

## Types d'authentification

### Pas d'authentification

Sélectionnez cette option pour les APIs publiques ne nécessitant pas d'identification.

### Token

Authentification par token (Bearer token, API Key, etc.).

**Format du champ Auth :**
```
headerName:token
```

**Exemples :**
- `Authorization:Bearer eyJhbGciOiJIUzI1NiIs...`
- `X-API-Key:ma-cle-api-123456`

### Basic Auth

Authentification HTTP Basic.

**Format du champ Auth :**
```
username:password
```

**Exemple :**
- `admin:monMotDePasse`

---

## Paramètres JSON

Le champ **Paramètres** permet d'envoyer des données dans le body de la requête au format JSON.

**Exemple :**
```json
{
    "startDate": "2024-01-01",
    "endDate": "2024-12-31",
    "limit": 1000
}
```

---

## Chemins d'accès (X Path / Y Path)

Ces champs permettent de spécifier quelles propriétés de la réponse JSON utiliser pour les axes X et Y des graphiques.

### Exemple de réponse API

```json
{
    "data": [
        {"date": "2024-01", "sales": 15000},
        {"date": "2024-02", "sales": 18500},
        {"date": "2024-03", "sales": 22000}
    ]
}
```

Pour ce cas :
- **Chemin X** : `date`
- **Chemin Y** : `sales`

---

## Certificats SSL

{: .warning }
> La désactivation de la vérification des certificats n'est pas recommandée en production.

L'option **Vérification des certificats** permet de :
- **Activer** : Vérifie la validité du certificat SSL (recommandé)
- **Désactiver** : Ignore les erreurs de certificat (utile pour le développement avec certificats auto-signés)

---

## Bonnes pratiques

- **Sécurité** : Ne stockez jamais de tokens sensibles en clair si possible
- **Timeout** : Tenez compte des temps de réponse des APIs externes
- **Limites** : Respectez les rate limits des APIs tierces
- **Cache** : Utilisez le rafraîchissement approprié pour éviter les appels excessifs

