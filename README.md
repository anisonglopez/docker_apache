# Docker Apache for Host Laravel

## How to install Step 1
```CMD
git clone https://github.com/anisonglopez/docker_apache.git
cd apache
cd app
git clone <your_git_repository> .
```
Example
```CMD
git clone 
 https://github.com/anisonglopez/laravel_example.git .
```

Remark: Must to have dot (.) after

## How to install Step 2
We have laravel project in your apache/app directory. Next step we must to cd to root docker project directory path.
```CMD
pwd
ls
<!-- Must to have docker-compose.yml in current command path-->
docker-compose up --build -d
<!-- or -->
docker-compose build --no-cache
```
Remark: Make sure have a laravel project in apache/app

## How to down system
```CMD
docker-compose down -v
```

## Execute compoer via docker exec
 ```CMD
 docker ps
<!-- find a container id -->
docker exec -it <container_id> bash
<!-- now  /var/www/html#-->
composer install
npm install
npm run dev
```

## Check your .env is available
example my env
```ENV
DB_CONNECTION=mysql
DB_HOST=docker_mariadb
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=secret
```