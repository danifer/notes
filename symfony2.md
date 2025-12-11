Symfony 2 framework setup with Composer, Doctrine ORM, console commands, cache, fixtures, migrations, and FOSUserBundle.

- Installed composer locally (http://getcomposer.org/download/)
- Used composer to create a new symfony project: php composer.phar create-project symfony/framework-standard-edition path/ 2.4.0 (sets up directory structure)
- Create a bundle for your "thing"
    php bin/console generate:bundle --namespace=Acme/StoreBundle
- Create app/logs and app/cache directories and set permissions to 777
  - Setup file Permissions ACLs for Debian (so www-data can edit/delete files):
    - https://help.ubuntu.com/community/FilePermissionsACLs
    - http://symfony.com/doc/current/book/installation.html#configuration-and-setup
- Configure the database in app/config/parameters.yml and app/config/config.yml
- Create the actual database: php bin/console doctrine:database:create
    Be sure to change the default collation and character set:
      collation-server = utf8_general_ci
      character-set-server = utf8
- Make entities for Doctrine Objects: http://symfony.com/doc/current/book/doctrine.html
- Create the database: php bin/console doctrine:schema:update --force


Commands:

Rebuild database from schema:
  php bin/console doctrine:schema:update --force

Get Symfony version:
  php bin/console --version

Clear cache:
  php bin/console cache:clear
  php bin/console cache:clear --env=prod --no-debug

Load fixtures:
  php bin/console doctrine:fixtures:load

Publish js/css resources managed by assetic (don't forget to clear the cache)
  php bin/console assetic:dump

Generate a new doctrine entity:
  php bin/console generate:doctrine:entity

FOSUserBundle console command to change a user password
  php bin/console fos:user:change-password testuser newp@ssword

Triger doctrine migrations
  php bin/console doctrine:migrations:migrate
