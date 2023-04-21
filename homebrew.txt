To restart postgresql after an upgrade:
    brew services restart postgresql

To migrate existing data from a previous major version of PostgreSQL run:
  brew postgresql-upgrade-database

To restart redis after an upgrade:
  brew services restart redis

The php.ini and php-fpm.ini file can be found in:
    /opt/homebrew/etc/php/7.4/

Switch between php versions
    brew unlink php@7.4
    brew link php@7.3
