Setelah menginstal laravel jalankan perintah berikut agar PHP-FPM di container punya izin nulis ke folder database/ storage/ dan bootstrap/cache/.

chmod -R 775 /var/www/storage
chmod -R 775 /var/www/bootstrap/cache
chmod -R 775 /var/www/database
chown -R www-data:www-data storage bootstrap/cache database

Setting database di .env :
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=laravel
