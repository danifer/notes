Make a new project
  symfony new my_project_name 3.4

Exclude version control:
  parameters.yml
  vendor/*
  cache/*
  logs/*

Configure your application in app/config/parameters.yml file.

Read the documentation at https://symfony.com/doc

Drop a database
  php bin/console doctrine:database:drop --force

Create a database
  php bin/console doctrine:database:create

Generate an entity interactively
  php bin/console doctrine:generate:entity

Validate data mapping
  php bin/console doctrine:schema:validate

Update the database schema
  php bin/console help doctrine:schema:update
    --force
    --dump-sql

List all routes
  php bin/console debug:router

List all available console commands
  php bin/console

Follow the log files in real time
    php bin/console server:log -vv

Working with parameters in the container
    $container->hasParameter('mailer.transport');
    $container->getParameter('mailer.transport');
    $container->setParameter('mailer.transport', 'sendmail');

Check if the user is authenticated before accessing the $this->getUser() method
  https://symfony.com/doc/3.4/security.html
    $this->denyAccessUnlessGranted('IS_AUTHENTICATED_FULLY');
    $this->container->get('security.authorization_checker')->isGranted('IS_AUTHENTICATED_FULLY')
    $this->container->get('security.authorization_checker')->isGranted('IS_AUTHENTICATED_REMEMBERED') || $this->container->get('security.authorization_checker')->isGranted('IS_AUTHENTICATED_FULLY')

created/updated timestamps on Doctrine entities:
  https://maltronic.io/2015/08/22/automating-created-updated-deleted-timestamps-with-doctrine/

FOSUserBundle Configuration:
  https://symfony.com/doc/master/bundles/FOSUserBundle/configuration_reference.html

Fixing the file permission issue on var/log; var/cache; var/session directories:
  https://symfony.com/doc/3.4/setup/file_permissions.html
     HTTPDUSER=$(ps axo user,comm | grep -E '[a]pache|[h]ttpd|[_]www|[w]ww-data|[n]ginx' | grep -v root | head -1 | cut -d\  -f1)
     sudo setfacl -dR -m u:"$HTTPDUSER":rwX -m u:$(whoami):rwX var
     sudo setfacl -R -m u:"$HTTPDUSER":rwX -m u:$(whoami):rwX var
