Sebelum build buat folder ./mysql/data dan ./src
mkdir -p mysql/data
mkdir -p src

docker compose up -d --build

docker compose exec -it app bash

composer create-project laravel/laravel .

Setelah menginstal laravel jalankan perintah berikut agar PHP-FPM di container punya izin nulis ke folder database/ storage/ dan bootstrap/cache/.

chmod -R 775 /var/www/storage
chmod -R 775 /var/www/bootstrap/cache
chmod -R 775 /var/www/database
chown -R www-data:www-data storage bootstrap/cache database

Setting di .env :

# Database

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=laravel

# Redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379

# Queue

QUEUE_CONNECTION=redis
