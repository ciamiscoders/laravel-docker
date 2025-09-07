1. Sebelum build buat folder ./mysql/data dan ./src

```
  mkdir -p mysql/data
  mkdir -p src
```

2. Build dan jalankan container

```
  docker compose up -d --build
```

3. Masuk ke root folder di container

```
  docker compose exec -it app bash
```

4. Install laravel

```
  composer create-project laravel/laravel .
```

5. Setelah menginstal laravel jalankan perintah berikut agar PHP-FPM di container punya izin nulis ke folder database/ storage/ dan bootstrap/cache/.

```
chmod -R 775 /var/www/storage
chmod -R 775 /var/www/bootstrap/cache
chmod -R 775 /var/www/database
chown -R www-data:www-data storage bootstrap/cache database
```

6. Sesuaikan setting di .env :

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=laravel

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379

QUEUE_CONNECTION=redis
