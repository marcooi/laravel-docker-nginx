- Clone Repository  
     `git clone https://github.com/marcooi/laravel-docker-2.git `

- Change this based on your preference

    == app:  ==
    image: istw-apps-img
    container_name: app_container
     networks:
      - app_network

    == NGINX: ==
    container_name: app_nginx
     ports:
      - 91:80
     networks:
      - app_network

    == horizon: ==
    image: istw-apps-img
    container_name: app_horizon
    networks:
      - app_network
    depends_on:
      - app
    
    == schedule-worker: ==
    image: istw-apps-img
    container_name: app_schedule_worker
    networks:
      - app_network

    networks:
        app_network:

- Build image
    ` docker compose build --no-cache `

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
     ` docker compose up -d `     

- masuk ke console container 
    ` docker compose exec app bash `


- install and run composer   
     ` composer install --optimize-autoloader --no-dev `  
     ` php artisan migrate `
     ` php artisan key:generate `
     ` composer dump-autoload `
     ` php artisan storage:link` 

     

