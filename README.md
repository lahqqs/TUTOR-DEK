# TUTOR-DEK
apt update -y
apt upgrade -y
apt install nginx -y
systemctl enable nginx
systemctl start nginx
systemctl status nginx
apt-add-repository ppa:ondrej/php -y
systemctl enable php8.0-fpm
systemclt start php8.0-fpm
apt install -y php8.0 php8.0-ctype php8.0-curl php8.0-dom php8.0-fileinfo php8.0-filter php8.0-hash php8.0-mbstring php8.0-openssl php8.0-pcre php8.0-pdo php8.0-session php8.0-tokenizer php8.0-xml php8.0-zip
apt install mariadb-server mariadb-client -y
systemctl enable mariadb
systemctl start mariadb
systemctl status mariadb
mysql_secure_installation
wget -O composer-setup.php https://getcomposer.org/installer
php composer-setup.php --install-dir=/usr/bin --filename=composer
cd /var/www/html
composer create-project laravel/laravel:^9.0 example-app
chown www-data:www-data /var/www/html -R
mysql -e "CREATE USER 'laravel'@'localhost' IDENTIFIED BY '<PASSWORD-HERE>';"
mysql -e "CREATE DATABASE laravel;"
mysql -e "GRANT ALL PRIVILEGES ON laravel.* to 'laravel'@'localhost';"
