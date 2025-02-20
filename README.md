## Setup

1. create .env from .env.example
````
cp .env.example .env
````
2. spin up database container
````
docker compose up db -d
````
3. install packages
````
composer install
````
4. generate key into .env APP_KEY
````
php artisan key:generate
````
5. run migration files
````
php artisan migrate
````
6. seed data into db
````
php artisan db:seed
````

## Publish
Serving laravel using all IPv4 addresses

````
php artisan serve --host=0.0.0.0
````