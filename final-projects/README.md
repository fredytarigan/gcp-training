# Setup Codeigniter in Compute Instance

## Pre-Setup

```bash
## install required software
sudo apt update -y
sudo apt install apache2 -y \
    && sudo apt install php -y \
    && sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip php-mysqlnd unzip curl -y

a2enmod rewrite
sudo systemctl restart apache2
```

## Codeigniter Setup

```bash
## download and setup codeigniter
cd /var/www/
rm -rf html
git clone https://github.com/fredytarigan/codeigniter.git
mv codeigniter html
chown -R www-data:www-data codeigniter
cd /var/www/html
```

## Configure connection to database

```bash
## edit database configuration file in: ./app/Config/Database.php
vi ./app/Config/Database.php

## change the value of database configuration at: public $default
public $default = [
        'DSN'      => '',
        'hostname' => '{{ replace with cloud sql mysql ip or endpoint }}',
        'username' => '{{ replace with cloud sql mysql username }}',
        'password' => '{{ replace with cloud sql mysql password }}',
        'database' => '{{ replace with cloud sql mysql database name }}',
        'DBDriver' => 'MySQLi',
        'DBPrefix' => '',
        'pConnect' => false,
        'DBDebug'  => (ENVIRONMENT !== 'production'),
        'charset'  => 'utf8',
        'DBCollat' => 'utf8_general_ci',
        'swapPre'  => '',
        'encrypt'  => false,
        'compress' => false,
        'strictOn' => false,
        'failover' => [],
        'port'     => 3306,
    ];

## leave another options with default value then save and exit
```