# Documentation SYD - Start Your Dashboard

Ce dossier contient la documentation utilisateur de SYD au format GitHub Pages avec le thème [Just the Docs](https://just-the-docs.github.io/just-the-docs/).

## Structure

```
docs/
├── _config.yml              # Configuration Jekyll
├── Gemfile                  # Dépendances Ruby
├── index.md                 # Page d'accueil
├── builder/                 # Documentation SYD Builder
│   ├── index.md            
│   ├── connecteurs/        # Bases de données, webservices, requêtes
│   ├── modules/            # Types de modules, affichage, datalabels
│   ├── dashboards/         # Création et layout
│   ├── formulaires/        # Champs et formulaires
│   ├── utilisateurs-groupes.md
│   ├── categories.md
│   └── geojson.md
├── visualizer/              # Documentation SYD Visualizer
│   ├── index.md
│   ├── authentification.md
│   ├── consultation.md
│   └── export.md
├── installation/            # Guide d'installation
│   └── index.md
└── assets/                  # Images et ressources
    └── img/
```

## Développement local

### Prérequis

- Ruby 2.7+
- Bundler

### Installation

```bash
cd docs
bundle install
```

### Lancer le serveur de développement

```bash
bundle exec jekyll serve
```

Accédez à `http://localhost:4000/syd/`

## Déploiement sur GitHub Pages

1. Poussez le dossier `docs/` sur votre dépôt GitHub
2. Dans les paramètres du dépôt, activez GitHub Pages
3. Sélectionnez la branche et le dossier `/docs`
4. Le site sera disponible à l'URL fournie par GitHub

## Ajouter des captures d'écran

1. Placez vos images dans `docs/assets/img/`
2. Utilisez la syntaxe Markdown :
   ```markdown
   ![Description]({{ site.baseurl }}/assets/img/mon-image.png)
   ```

## Personnalisation

- **Couleurs** : Modifiez `color_scheme` dans `_config.yml`
- **Logo** : Ajoutez votre logo dans `assets/img/` et référencez-le
- **Footer** : Modifiez `footer_content` dans `_config.yml`

## Thème

Cette documentation utilise le thème [Just the Docs](https://just-the-docs.github.io/just-the-docs/) qui offre :
- Navigation latérale automatique
- Recherche intégrée
- Responsive design
- Table des matières automatique

