## Setup Server
We are using DigitalOcean droplet with Ubuntu 22.04 for testing the application.

php version that is automatically install using command apt is php8.3

1. install docker
    ````
    snap install docker
    ````
2. install php
    ````
    sudo apt install -y php-cli unzip php-mbstring php-xml php-bcmath php-mysql
    ````
3. clone app
    ````
    cd ~
    git clone https://github.com/veryresto/travellist-demo03.git
    ````

## Setup App

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