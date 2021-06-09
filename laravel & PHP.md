# Install Laravel & PHP in Ubuntu



#### Step 1: Log in via SSH and Update your System
```
ssh root@IP_ADDRESS -p PORT_NUMBER
apt-get update -y
apt-get upgrade -y
```

#### Step 2: Install Apache and PHP
```
apt-get install apache2 php7.4 libapache2-mod-php7.4 php7.4-curl php-pear php7.4-gd php7.4-dev php7.4-zip php7.4-mbstring php7.4-mysql php7.4-xml curl -y


systemctl start apache2
systemctl enable apache2

```


#### Step 3: Install Composer
```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer

composer --version
```
#### Step 4: Install Laravel Framework
```
cd /var/www/html
composer create-project laravel/laravel laravelapp --prefer-dist

```
#### Once the installation is finished, you should see the following output:



```
Creating a "laravel/laravel" project at "./laravelapp"
Installing laravel/laravel (v7.6.0)
- Installing laravel/laravel (v7.6.0): Loading from cache
Generating optimized autoload files
> Illuminate\Foundation\ComposerScripts::postAutoloadDump
> @php artisan package:discover --ansi
Discovered Package: facade/ignition
Discovered Package: fideloper/proxy
Discovered Package: fruitcake/laravel-cors
Discovered Package: laravel/tinker
Discovered Package: nesbot/carbon
Discovered Package: nunomaduro/collision
Package manifest generated successfully.
31 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
> @php artisan key:generate --ansi
Application key set successfully.
```

#### Next, change the directory to the laravelapp directory and run the following command to verify that all components were successfully installed:
```
cd laravelapp
php artisan
```
```
You should see the following output:

Laravel Framework 7.11.0
Usage:
command [options] [arguments]
Options:
-h, --help Display this help message
-q, --quiet Do not output any message
-V, --version Display this application version
--ansi Force ANSI output
--no-ansi Disable ANSI output
-n, --no-interaction Do not ask any interactive question
--env[=ENV] The environment the command should run under
-v|vv|vvv, --verbose Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

#### Next, change the ownership of the laravelapp directory and give proper permissions to the storage directory with the following command:

```
chown -R www-data:www-data /var/www/html/laravelapp
chmod -R 775 /var/www/html/laravelapp/storage
```

#### Step 5: Configure Apache to Serve Laravel App

```
Next, create a new Apache virtual host configuration file to serve the Laravel app.

nano /etc/apache2/sites-available/laravel.conf

Add the following lines:


<VirtualHost *:80>
ServerName laravel.example.com
ServerAdmin admin@example.com
DocumentRoot /var/www/html/laravelapp/public
<Directory /var/www/html/laravelapp>
AllowOverride All
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

#### Save and close the file when you are finished. Then, enable the Apache virtual host and rewrite module with the following command:

```
a2ensite laravel.conf
a2enmod rewrite

```

#### Finally, restart the Apache service to implement the changes:
```
systemctl restart apache2
```
#### Step 6: Access Laravel App
```
At this point, your Laravel application is installed and configured. Now, open your web browser and type the URL http://laravel.example.com. You should see the Laravel default page on the following screen:

installing laravel on ubuntu 20.04

Congratulations! you have successfully installed the Laravel framework on Ubuntu 20.04 VPS.
```
