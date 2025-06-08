- Clone Repository  
     `git clone https://github.com/marcooi/laravel-docker-2.git `

- Set Permission 
    <!-- ` sudo chown -R 1000:1000 ./src ` -->

    ` sudo chown -R :www-data ./src `
    ` sudo chmod -R g+rw ./src `
    ` sudo chmod g+s ./src `
 

- cd src  
 
- copy .env.example to .env  
     `cp .env.example .env`

- edit .env  
    `nano .env`  

   Edit value this section  


- move up one folder  
     `cd ..`  

- run docker compose  
     `docker-compose up --build -d`     

- masuk ke console container 
    ` docker-compose exec app bash `


- install and run composer   
     <!-- `docker-compose exec app composer update --optimize-autoloader --no-dev`   -->
     `docker-compose exec app composer install --optimize-autoloader --no-dev`  
     `docker-compose exec app php artisan key:generate`  
     `docker-compose exec app composer dump-autoload`  
     `docker-compose exec app php artisan horizon:publish`

     `docker-compose exec app php artisan cache:forget spatie.permission.cache` 
     `docker-compose exec app php artisan cache:clear` 

     <!-- `docker-compose exec app php artisan cache:clear`  
     `docker-compose exec app php artisan config:cache`   
     `docker-compose exec app php artisan route:cache`  
     `docker-compose exec app php artisan view:cache`   -->
     
     `docker exec -it app_app php artisan optimize:clear` 
     `docker exec -it app_app php artisan route:cache`  
     `docker exec -it app_app php artisan config:cache` 
     `docker exec -it app_app php artisan view:cache` 
     `docker exec -it app_app php artisan storage:link` 

     `docker exec -it app_app php artisan view:cache` 

     <!-- `docker exec -it app php artisan optimize:clear` 
     `docker exec -it app php artisan optimize`  -->
     

     <!-- `docker run --rm -v $(pwd):/app composer/composer install` -->
     

