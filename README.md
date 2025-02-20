References:
- [How To Install and Configure Laravel with Nginx on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-laravel-with-nginx-on-ubuntu-20-04)
- [How To Install and Use Composer on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-set-up-laravel-with-docker-compose-on-ubuntu-20-04)

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
3. install composer
    ````
    cd ~
    curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
    sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
    ````
4. clone app
    ````
    cd ~
    git clone https://github.com/veryresto/travellist-demo03.git
    ````

## Setup App
Ensure you are in root project directory
````
cd ~/travellist-demo03
````


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