# laravel-environment

This is a Laravel environment designed to be used with Docker in Windows.

### Prerequisites

You need to have Docker for Windows installed and properly set up with shared drives.

## Setup Instructions

1. Create repo from this template repository
1. Clone repo onto a drive that is shared with Docker
1. Run the following commands (based on PowerShell):

```
Copy-Item .env.example .env
docker-compose up --build -d
cd src
Copy-Item .env.example .env
cd ..
docker-compose exec app /bin/bash -c "composer install"
docker-compose exec app /bin/bash -c "php artisan key:generate"
docker-compose exec app /bin/bash -c "php artisan migrate"
docker-compose exec node /bin/bash -c "npm install && npm run dev"
``` 

A base Laravel installation should now be available at `http://localhost:50000`

### Additional tools

PHP MyAdmin can be found at `http://localhost:50001`

The setup uses a mailcatcher to handle mail. This can be found at `http://localhost:50002`

## Running tests

To run unit tests, the following command should be ran:

```
docker-compose exec app /bin/bash -c "vendor/bin/phpunit"
```

To run browser tests, use the following command:

```
docker-compose exec app /bin/bash -c "php artisan dusk"
```

## Notice

**This setup is intended for local development only and is not suitable for a production environment** 