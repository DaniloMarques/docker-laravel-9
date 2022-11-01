# Docker with Laravel 9

## Used technologies
- PHP 8.1
- Laravel 9.x
- Docker

## Requirements

- **Docker:** Make sure docker and docker-compose are installed on your computer (for instructions on how to install docker go to the following link [How to install docker engine](https://docs.docker.com/engine/install/)).


## Download the project

1. Clone the repository

2. Remove versioning
    ```sh
    rm -rf .git/
    ```

## Installation and running the project

1. Access the project directory.

2. Update the .env file to connect with docker containers
    ```dosini
    APP_NAME=ProjectName
    APP_URL=http://localhost:8989
    
    DB_CONNECTION=mysql
    DB_HOST=mysql
    DB_PORT=3306
    DB_DATABASE=name_you_want
    DB_USERNAME=root
    DB_PASSWORD=root
    
    BROADCAST_DRIVER=log
    CACHE_DRIVER=redis
    FILESYSTEM_DISK=local
    QUEUE_CONNECTION=sync
    SESSION_DRIVER=redis
    SESSION_LIFETIME=120
    
    REDIS_HOST=redis
    REDIS_PASSWORD=null
    REDIS_PORT=6379
    ```

3. Up docker containers
    ```sh
    docker-compose up -d
    ```

4. Access `app` container to install project dependencies
    ```sh
    docker-compose exec app bash
    ```

5. Install project dependencies
    ```sh
    composer install
    ```

6. Generate key project
    ```sh
    php artisan key:generate
    ```

7. Run migrations to create the DB
    ```sh
    php artisan migrate
    ```

8. Access the project page

   [http://localhost:8989](http://localhost:8989)

## Testing the project

The project already has unit tests (PHPUnit) that test all available endpoints and also other system features.

### To run the unit tests, perform the following steps:

1. With the system running, access the docker container `app` via bash.
    ```sh
    docker-compose exec app bash
    ```

2. Run the command to run the unit tests.
    ```sh
    php artisan test
    ```