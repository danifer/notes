Sample gitignore template file for Symfony projects including vendor, cache, env files, and IDE configurations.

###> git ###
!/**/.gitkeep
###< git ###

###> symfony/framework-bundle ###
/**/.env.local
/**/.env.local.php
/**/.env.*.local
/var
/vendor
###< symfony/framework-bundle ###

# Files
*.DS_Store
*.dump
*.sql
*.swp
*.xlsx

###> IDE Files ###
/.idea
###< IDE Files ###
