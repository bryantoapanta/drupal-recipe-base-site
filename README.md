## Instalación

Añade estas lineas a la clave`repositories` del fichero composer.json:


```json
        {
            "type": "vcs",
            "url": "https://github.com/bryantoapanta/drupal-recipe-base-site.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-content-moderation.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-webforms.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-content-type-basic-page.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-content-type-landing.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-site-basic.git"
        },
        {
            "type": "vcs",
            "url": "https://git.drupalcode.org/issue/media_responsive_thumbnail-3431911.git"
        },
        {
            "type": "vcs",
            "url": "https://git.drupalcode.org/issue/layout_builder_at-3431569.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-base.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-digital-experience.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-seo-analytics.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-development.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-multilingual.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-security-logging.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-solr.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-admin-theme-gin.git"
        },
        {
            "type": "vcs",
            "url": "https://gitlab.metadrop.net/metadrop-public-repositories/recipes/drupal-recipe-frontend-theme-artisan.git"
        },
```

Añade los siguientes parches:

```json
        "patches": {
            "drupal/vlsuite": {
                "Add bundle fields to entity field storage info - https://www.drupal.org/project/vlsuite/issues/3476173": "patches/vlsuite-3476173-entity-field-storage-info-1.patch",
                "Allow vlsuite demo /shuttle to be installed through recipes": "patches/vlsuite-3490677-2.patch"
            },
            "drupal/gin": {
                "Js error when saving reference field - https://www.drupal.org/project/gin/issues/3492920": "patches/gin-3492920-1.patch"
            },
            "drupal/core": {
                "Stream wrappers not registered when installing module's default config - https://www.drupal.org/project/drupal/issues/3416735": "https://git.drupalcode.org/project/drupal/-/merge_requests/10421.diff",
                "Allow recipe command to write to the container ensuring that cache does not be cleared after a recipe installs a module - https://www.drupal.org/project/drupal/issues/3315694": "patches/drupal-core-3315694-1.patch",
                "Call to undefined method isLayoutBuilderEnabled()": "https://www.drupal.org/files/issues/2022-09-05/3277728-7.patch",
                "RecipeConfigInstaller should process translation config files - https://www.drupal.org/project/distributions_recipes/issues/3453331": "patches/drupal-core-3453331-recipe-translations.patch"

            }
        }
```

Requiere los paquetes necesarios para instalar la receta:

```bash
composer require bryantoapanta/drupal-recipe-base-site
composer require drupal/media_responsive_thumbnail:"dev-3431911-automated-drupal-11#37e476ed5555d8b4d63c273a581da67ebd2ee445 as 1.x-dev"
composer require drupal/layout_builder_at:"dev-project-update-bot-only#1711072acdd1316d2648372557bf4273a9352e66 as 2.x-dev"
composer require --dev metadrop/drupal-dev
```

Instala la receta:

```
drush cr
drush recipe recipes/drupal-recipe-base-site
```


Desempaqueta la receta:

```bash
  composer unpack bryantoapanta/drupal-recipe-base-site
  composer unpack metadrop/drupal-recipe-basic-site
  composer unpack metadrop/drupal-recipe-base
  composer unpack metadrop/drupal-recipe-development
  composer unpack metadrop/drupal-recipe-digital-experience
  composer unpack metadrop/drupal-recipe-multilingual
  composer unpack metadrop/drupal-recipe-security-logging
  composer unpack metadrop/drupal-recipe-seo-analytics
  composer unpack metadrop/drupal-recipe-admin-theme-gin
  composer unpack metadrop/drupal-recipe-frontend-theme-artisan
  composer unpack metadrop/drupal-recipe-content-moderation
  composer unpack metadrop/drupal-recipe-content-type-basic-page
  composer unpack metadrop/drupal-recipe-content-type-landing
  composer unpack metadrop/drupal-recipe-webforms
```

Borra los repositorios añadidos manualmente del composer.json.