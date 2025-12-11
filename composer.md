PHP Composer commands for package management including show, search, require, and dependency information.

Show installed packages
  php composer.phar show

Search for packages
  php composer.phar search [package name]

Show information from a package
  php composer.phar show -a doctrine/doctrine-fixtures-bundle

Require a new package in your config
  php composer.phar require --dev doctrine/doctrine-fixtures-bundle