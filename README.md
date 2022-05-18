
# Docker Magento 2.4.3-p1 Open Source (CE) 01-2022

Docker container for Magento 2.4.3-p1 development including :

  - PHP 7.4
  - Apache 2.4
  - MYSQL 8
  - Varnish 6 FPC  
  - RabbitMQ  
  - PhpMyAdmin
  - memcached
  - ELASTIC search 7.x
  - REDIS Session, System, FPC
  - Scaleable php-apache service

## Installation

### Modify settings in Docker Desktop
Resources > ADVANCDED: Increase Memory to ~8GB
Resources > FILE SHARING: Add a new path for `/home`

### Modify vHosts
add a new entry in /etc/hosts
`127.0.0.1 ::1 magento2.dev.local`

### Clone this repo
### EDIT .env
CONTAINERDATA
MAGENTO_REPO_USERNAME
MAGENTO_REPO_PASSWORD

### Build/Launch
`cd magento2`
`docker-compose build`
`docker-compose up -d`

### Configure
(ssh into container)
`docker-compose exec -u magento php-apache bash`

(Install Magento)
`install-magento`

(Install sample data)
`install-sampledata`

(Disable 2FA for testing)
`bin/magento module:disable Magento_TwoFactorAuth`

(Fix layout issues with demo data)
`cp /var/www/dev/magento2/vendor/magento/module-cms-sample-data/fixtures/styles.css /var/www/dev/magento2/pub/media/`

## Test

 - Admin
http://magento2.dev.local/admin  
 - Frontend
http://magento2.dev.local  
 - CLI
`docker-compose exec -u magento php-apache bash`

