Symfony 1.4 framework setup commands for project generation, Doctrine ORM, modules, authentication, and templates.

---

Setup a new project:
php /home/www/lib/symfony-1.4.4/data/bin/symfony generate:project ecart
php symfony generate:app frontend
chmod 777 cache/ log/

php symfony cc

php symfony configure:database --name=doctrine --class=sfDoctrineDatabase "mysql:host=localhost;dbname=jobeet" root mYsEcret

php symfony doctrine:build-model

php symfony doctrine:build-sql

php symfony doctrine:insert-sql

php symfony doctrine:build-all

php symfony doctrine:build-all-reload

php symfony doctrine:generate-module --with-show --non-verbose-templates frontend create LtLink

php symfony guard:create-user admin ltlakdj15681531jnaljkdn

php symfony guard:promote admin

php symfony plugin:install sfDoctrineGuardPlugin

#Make a blank module
php symfony generate:module frontend mymodule

#Check authentication in a template
<?php if ($sf_user->isAuthenticated()): ?>

#Retrieve flash info from user session in template
<?php if ($sf_user->hasFlash('notice')): ?>
<div class="flash_notice"><?php echo $sf_user->getFlash('notice') ?></div>
<?php endif; ?>

<?php if ($sf_user->hasFlash('error')): ?>
<div class="flash_error"><?php echo $sf_user->getFlash('error') ?></div>
<?php endif; ?>
