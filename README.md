# Symfony 5 User/Security Bootstrap

### Setup env with full docker - useful for Ubuntu/Mac development
Start docker with:
```
cp docker-compose-dist.yml docker-compose.yml
docker-compose build
docker-compose up -d
docker-compose exec php composer install
```

### Setup env with local php - useful for Windows WSL development

Dependencies:
php7.4, composer, symfony-cli

Start docker with (comment out nginx, php, frontend):
```
cp docker-compose-dist.yml docker-compose.yml
docker-compose up -d
composer install
```

Adjust env settings - uncomment below (default db name is `default`):
```
cp .env.dev .env.dev.local
#DATABASE_URL=mysql://root:P@ssw0rd@127.0.0.1:3307/default
``` 
Prepare dev database with:
```
echo 'DATABASE_URL=mysql://root:P@ssw0rd@127.0.0.1:3307/default' >> .env.local
bash reset_dev_db.sh
```
Start local server with:
```
symfony serve
```

### Users created from fixtures

Users are created with credentials:
```
root@root.dev / root (admin user)
user@user.dev / user (regular user)
```

### Where to go from here?
It's your choice to build API or CRUD - whatever suites your needs best!

CRUD - https://symfony.com/doc/current/security/form_login_setup.html

API - https://api-platform.com/docs/distribution/

Docker is prepared to handle redis, rabbit, yarn encore - just uncomment in `docker-compose.yml`.

You will find more configuration in `/docker`. 
