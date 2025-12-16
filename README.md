Starshop Symfony Project
=======================

Ce repository a été créé pour m’exercer à Symfony dans le cadre de mon stage.

Cours suivis
------------

- https://symfonycasts.com/screencast/symfony
- https://symfonycasts.com/screencast/symfony-fundamentals
- https://symfonycasts.com/screencast/symfony-doctrine

Documentation officielle
-----------------------

- https://symfony.com/doc
- https://twig.symfony.com/doc/3.x
- https://symfony.com/doc/current/doctrine.html

Installation et configuration de Symfony
---------------------------------------

Vérifications initiales :
- symfony --help
- symfony check:req

Créer un nouveau projet :
- symfony new directory-name          # projet minimal
- symfony new directory-name --webapp # projet complet avec modules web

Se déplacer dans le projet :
- cd directory-name

Vérifier les fichiers :
- dir   # Windows
- ls    # Linux/macOS

Lancer le serveur local :
symfony serve
# La première fois, accepter le certificat SSL
# Stopper le serveur : Ctrl + C

Git
---

Symfony initialise automatiquement un dépôt Git et un commit initial :

- git status
- git log
- git ls-files

Pour connecter le projet à un repo distant :
- git remote add origin <URL_DU_REPO>
- git push -u origin master  # ou master:main selon GitHub

Composer & dépendances
---------------------

Installer des packages :
- composer require symfony/http-client
- composer require cs-fixer-shim
- composer require twig
- composer require debug
- composer require serializer
- composer require symfony/asset-mapper
- composer require symfony/asset
- composer require symfonycasts/tailwind-bundle
- composer require symfony/stimulus-bundle
- composer require symfony/ux-turbo
- composer require symfony/orm-pack
- composer require --dev symfony/maker-bundle
- composer require --dev orm-fixtures
- composer require --dev foundry
- composer require babdev/pagerfanta-bundle pagerfanta/doctrine-orm-adapter
- composer require stof/doctrine-extensions-bundle
- composer require knplabs/knp-time-bundle

CS-Fixer :
`./vendor/bin/php-cs-fixer fix`

Symfony Console
---------------

Afficher toutes les commandes :
- php bin/console

Générer une commande :
- symfony console make:command
# Ex : app:ship-report

Debug :
- php bin/console debug:router
- php bin/console debug:twig
- php bin/console debug:container
- php bin/console debug:autowiring
- php bin/console debug:config framework
- php bin/console debug:dotenv

Assets et Tailwind
-----------------

- php bin/console tailwind:init
- php bin/console tailwind:build -w

Doctrine
--------

Base de données :
- php bin/console doctrine:database:create
- php bin/console doctrine:schema:validate
- php bin/console doctrine:migrations:migrate
- php bin/console doctrine:migrations:list
- symfony console doctrine:query:sql 'SELECT * FROM starship'

Entités :
- php bin/console make:entity
- php bin/console make:factory

Fixtures :
- symfony console doctrine:fixtures:load

Gestion du cache
----------------

Voir les pools disponibles :
- php bin/console cache:pool:list

Vider un cache précis :
- php bin/console cache:pool:clear cache.app

Passer en prod :
- php bin/console asset-map:compile
- php bin/console cache:clear --env=prod

# En DEV : `cache.adapter.array`
# En PROD : `cache.adapter.filesystem` (config/packages/cache.yaml)

Commands Symfony spécifiques pour Starship
------------------------------------------

Supprimer un vaisseau :
- symfony console make:command
# Nom : app:ship:remove
- symfony console app:ship:remove <slug_du_vaisseau>

Check-in d’un vaisseau :
- symfony console make:command
# Nom : app:ship:check-in
- symfony console app:ship:check-in <slug_du_vaisseau>

Vérifier les vaisseaux avec un statut donné :
- symfony console doctrine:query:sql "SELECT slug, status FROM starship WHERE status = 'completed'"

Notes utiles
------------

Vérifier les services (HTTP client, cache…) :
- php bin/console debug:autowiring

Vérifier les requêtes :
https://127.0.0.1:8000/_profiler/

Logs en temps réel sous PowerShell :
- Get-Content var\log/dev.log -Wait

Slugs : versions lisibles des noms de vaisseaux pour les URLs.
