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
```

## Configure connection to database