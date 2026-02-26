---
layout: default
title: Installation
nav_order: 4
has_children: true
permalink: /installation/
---

# Installation
{: .fs-9 }

Déploiement de SYD Builder et Visualizer
{: .fs-6 .fw-300 }

---

## Prérequis techniques

### Serveur web

| Composant | Version minimale |
|:----------|:-----------------|
| **Apache** ou **Nginx** | Apache 2.4+ / Nginx 1.18+ |
| **PHP** | 7.4 ou supérieur |
| **Extensions PHP** | pdo, pdo_mysql, json, mbstring |

### Base de données

| SGBD | Version minimale |
|:-----|:-----------------|
| **MySQL** | 5.7+ |
| **MariaDB** | 10.3+ |
| **DB2** | Selon version IBM |

### Navigateurs supportés

| Navigateur | Version |
|:-----------|:--------|
| **Google Chrome** | Dernières versions |
| **Mozilla Firefox** | Dernières versions |
| **Microsoft Edge** | Dernières versions |
| **Safari** | Dernières versions |

---

## Architecture

SYD se compose de plusieurs modules :

```
SYD/
├── syd-builder/
│   ├── api-builder/      # API REST du Builder
│   ├── front-builder/    # Interface web du Builder
│   ├── setup-builder/    # Assistant d'installation
│   └── config/           # Configuration partagée
│
└── syd-visualizer/
    ├── api-visualizer/   # API REST du Visualizer
    ├── front-visualizer/ # Interface web du Visualizer
    ├── setup-visualizer/ # Assistant d'installation
    └── config/           # Configuration partagée
```

---

## Installation rapide

### 1. Téléchargement

Téléchargez les sources de SYD depuis le dépôt officiel.

### 2. Configuration du serveur web

Configurez votre serveur web pour pointer vers les dossiers `public/` des différents modules :

**Exemple Apache (Virtual Host) :**
```apache
# Builder Front
<VirtualHost *:80>
    ServerName builder.mondomaine.fr
    DocumentRoot /var/www/syd/syd-builder/front-builder/public
</VirtualHost>

# Builder API
<VirtualHost *:80>
    ServerName api-builder.mondomaine.fr
    DocumentRoot /var/www/syd/syd-builder/api-builder/public
</VirtualHost>

# Visualizer Front
<VirtualHost *:80>
    ServerName visualizer.mondomaine.fr
    DocumentRoot /var/www/syd/syd-visualizer/front-visualizer/public
</VirtualHost>

# Visualizer API
<VirtualHost *:80>
    ServerName api-visualizer.mondomaine.fr
    DocumentRoot /var/www/syd/syd-visualizer/api-visualizer/public
</VirtualHost>
```

### 3. Installation des dépendances

```bash
# Builder
cd syd-builder/api-builder && composer install
cd ../front-builder && composer install

# Visualizer
cd ../../syd-visualizer/api-visualizer && composer install
cd ../front-visualizer && composer install
```

### 4. Assistant de configuration

Accédez à l'assistant d'installation :
- **Builder** : `http://votre-serveur/setup-builder/`
- **Visualizer** : `http://votre-serveur/setup-visualizer/`

L'assistant vous guidera pour :
- Configurer la connexion à la base de données
- Créer les tables nécessaires
- Configurer les paramètres de l'application

---

## Configuration

### Fichier de configuration

Copiez le fichier de configuration exemple :
```bash
cp config/config.inc.sample.php config/config.inc.php
```

Éditez le fichier `config/config.inc.php` avec vos paramètres.

### Paramètres principaux

| Paramètre | Description |
|:----------|:------------|
| `DB_HOST` | Adresse du serveur de base de données |
| `DB_NAME` | Nom de la base de données SYD |
| `DB_USER` | Utilisateur de la base |
| `DB_PASSWORD` | Mot de passe de la base |
| `FRONT_ROOT` | URL racine du frontend |
| `API_ROOT` | URL racine de l'API |

---

## Base de données

### Création de la base

```sql
CREATE DATABASE syd CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Import du schéma

Les scripts SQL sont disponibles dans `config/db/` :
- `schema_mysql.sql` : Pour MySQL/MariaDB
- `schema_db2.sql` : Pour DB2

---

## Vérification

Après installation, vérifiez :

1. ✅ Accès à l'interface Builder
2. ✅ Accès à l'interface Visualizer
3. ✅ Connexion à la base de données
4. ✅ Création d'un premier utilisateur administrateur
5. ✅ Création d'un dashboard de test

---

## Support

En cas de difficulté lors de l'installation :

- Consultez les logs dans les dossiers `logs/`
- Vérifiez les permissions des fichiers
- Consultez la documentation complète
- Contactez le support CFD Innovation

