Del fitxer [comandes.txt](./comandes.txt) podeu substituir les següents cadenes.

|Cadena a substituir|Informació de la columna|Exemple|
|---|---|---|
|**```<CognomAlumne1>-<CognomAlumne2>```**|Nom de la base de dades|**```nieto-pardo```**|
|**```<nom de la vostra base de dades>```**|Nom de la base de dades|**```nieto-pardo```**|
|**```<usuari de connexió a la base de dades>```**|Usuari de connexió a la base de dades|**```nietopardo```**|
|**```<contrasenya de l'usuari de connexió>```**|Contrasenya de l'usuari de connexió|**```nietopardo123```**|

Un cop fet aquestes substitucions, si ho heu fet bé, ja teniu totes les comandes que cal que executeu per fer l'activitat.

```
sudo sed -i 's/Cadena a substituir/Informació de la columna/g' comandes-exemple.txt
```

Exemple de comandes per fer les substitucions.

Executem una comanda previa per veure el contingut del fitxer **```comandes-exemple.txt```**. 

* **Comanda a executar**:

```
cat comandes-exemple.txt
```

* **Sortida**:

<pre>
sudo docker image list |grep php:7.0-fpm

sudo docker image list |grep nginx

sudo docker image list |grep mariadb

sudo docker pull php:7.0-fpm

sudo docker pull nginx

sudo docker pull mariadb

sudo mkdir ~/<CognomAlumne1>-<CognomAlumne2>

cd ~/<CognomAlumne1>-<CognomAlumne2>

sudo mkdir ~/<CognomAlumne1>-<CognomAlumne2>/webSrv

sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/webSrv/Dockerfile

FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf

sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/webSrv/default.conf

server {  

     listen 80 default_server;  
     root /var/www/html;  
     index index.html index.php;  

     charset utf-8;  

     location / {  
      try_files $uri $uri/ /index.php?$query_string;  
     }  

     location = /favicon.ico { access_log off; log_not_found off; }  
     location = /robots.txt { access_log off; log_not_found off; }  

     access_log off;  
     error_log /var/log/nginx/error.log error;  

     sendfile off;  

     client_max_body_size 100m;  

     location ~ .php$ {  
      fastcgi_split_path_info ^(.+.php)(/.+)$;  
      fastcgi_pass php:9000;  
      fastcgi_index index.php;  
      include fastcgi_params;
      fastcgi_read_timeout 300;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  
      fastcgi_intercept_errors off;  
      fastcgi_buffer_size 16k;  
      fastcgi_buffers 4 16k;  
    }  

     location ~ /.ht {  
      deny all;  
     }  
    }	
    
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/<CognomAlumne1>-<CognomAlumne2>/phpSrv/

sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/phpSrv/Dockerfile

FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/docker-compose.yml

version: "3.9"
services:
   nginx:
     build: ./webSrv/
     ports:
       - 80:80
  
     volumes:
         - ./phpSrv/:/var/www/html/

   php:
     build: ./phpSrv/
     expose:
       - 9000
     volumes:
        - ./phpSrv/:/var/www/html/


   db:    
      image: mariadb  
      volumes: 
        -    mysql-data:/var/lib/mysql
      environment:  
       MYSQL_ROOT_PASSWORD: mariadb
       MYSQL_DATABASE: <nom de la vostra base de dades> 

volumes:
    mysql-data:
    
cd ~/<CognomAlumne1>-<CognomAlumne2>/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti <CognomAlumne1>-<CognomAlumne2>-db-1 bash

mariadb -u root -pmariadb

CREATE USER '<usuari de connexió a la base de dades>'@'%' IDENTIFIED BY '<Contrasenya de l'usuari de connexió>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO '<usuari de connexió a la base de dades>'@'%';

FLUSH PRIVILEGES;

show databases;

use <nom de la vostra base de dades>;

CREATE TABLE products(
  id mediumint(8) unsigned NOT NULL auto_increment,
  Name varchar(255) default NULL,
  Price varchar(255) default NULL,
  ImageUrl varchar(255) default NULL,
  PRIMARY KEY (id)
) AUTO_INCREMENT=1; 

INSERT INTO products (Name,Price,ImageUrl)
VALUES ("Laptop","100","c-1.png"),
       ("Drone","200","c-2.png"),
       ("VR","300","c-3.png"),
       ("Tablet","50","c-5.png"),
       ("Watch","90","c-6.png"),
       ("Phone Covers","20","c-7.png"),
       ("Phone","80","c-8.png"),
       ("Laptop","150","c-4.png");
       
exit

exit

cd ~/<CognomAlumne1>-<CognomAlumne2>/phpSrv

sudo vi index.php

$link = mysqli_connect('db', '<usuari de connexió a la base de dades>', '<contrasenya de l'usuari de connexió>', '<nom de la vostra base de dades>');

</pre>


## Primera substitució

|Cadena a substituir|Informació de la columna|Exemple|
|---|---|---|
|**```<CognomAlumne1>-<CognomAlumne2>```**|Nom de la base de dades|**```nieto-pardo```**|

* **Comanda a executar**:


```
sudo sed -i 's/<CognomAlumne1>-<CognomAlumne2>/nieto-pardo/g' comandes-exemple.txt
```

Executem una comanda per veure com ha quedat el contingut del fitxer **```comandes-exemple.txt```**. 

* **Comanda a executar**:

```
cat comandes-exemple.txt
```

* **Sortida**:

<pre>
sudo docker image list |grep php:7.0-fpm

sudo docker image list |grep nginx

sudo docker image list |grep mariadb

sudo docker pull php:7.0-fpm

sudo docker pull nginx

sudo docker pull mariadb

sudo mkdir ~/nieto-pardo

cd ~/nieto-pardo

sudo mkdir ~/nieto-pardo/webSrv

sudo vi ~/nieto-pardo/webSrv/Dockerfile

FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf

sudo vi ~/nieto-pardo/webSrv/default.conf

server {  

     listen 80 default_server;  
     root /var/www/html;  
     index index.html index.php;  

     charset utf-8;  

     location / {  
      try_files $uri $uri/ /index.php?$query_string;  
     }  

     location = /favicon.ico { access_log off; log_not_found off; }  
     location = /robots.txt { access_log off; log_not_found off; }  

     access_log off;  
     error_log /var/log/nginx/error.log error;  

     sendfile off;  

     client_max_body_size 100m;  

     location ~ .php$ {  
      fastcgi_split_path_info ^(.+.php)(/.+)$;  
      fastcgi_pass php:9000;  
      fastcgi_index index.php;  
      include fastcgi_params;
      fastcgi_read_timeout 300;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  
      fastcgi_intercept_errors off;  
      fastcgi_buffer_size 16k;  
      fastcgi_buffers 4 16k;  
    }  

     location ~ /.ht {  
      deny all;  
     }  
    }	
    
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/nieto-pardo/phpSrv/

sudo vi ~/nieto-pardo/phpSrv/Dockerfile

FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

sudo vi ~/nieto-pardo/docker-compose.yml

version: "3.9"
services:
   nginx:
     build: ./webSrv/
     ports:
       - 80:80
  
     volumes:
         - ./phpSrv/:/var/www/html/

   php:
     build: ./phpSrv/
     expose:
       - 9000
     volumes:
        - ./phpSrv/:/var/www/html/


   db:    
      image: mariadb  
      volumes: 
        -    mysql-data:/var/lib/mysql
      environment:  
       MYSQL_ROOT_PASSWORD: mariadb
       MYSQL_DATABASE: <nom de la vostra base de dades> 

volumes:
    mysql-data:
    
cd ~/nieto-pardo/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti nieto-pardo-db-1 bash

mariadb -u root -pmariadb

CREATE USER '<usuari de connexió a la base de dades>'@'%' IDENTIFIED BY '<Contrasenya de l'usuari de connexió>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO '<usuari de connexió a la base de dades>'@'%';

FLUSH PRIVILEGES;

show databases;

use <nom de la vostra base de dades>;

CREATE TABLE products(
  id mediumint(8) unsigned NOT NULL auto_increment,
  Name varchar(255) default NULL,
  Price varchar(255) default NULL,
  ImageUrl varchar(255) default NULL,
  PRIMARY KEY (id)
) AUTO_INCREMENT=1; 

INSERT INTO products (Name,Price,ImageUrl)
VALUES ("Laptop","100","c-1.png"),
       ("Drone","200","c-2.png"),
       ("VR","300","c-3.png"),
       ("Tablet","50","c-5.png"),
       ("Watch","90","c-6.png"),
       ("Phone Covers","20","c-7.png"),
       ("Phone","80","c-8.png"),
       ("Laptop","150","c-4.png");
       
exit

exit

cd ~/nieto-pardo/phpSrv

sudo vi index.php

$link = mysqli_connect('db', '<usuari de connexió a la base de dades>', '<contrasenya de l'usuari de connexió>', '<nom de la vostra base de dades>');

</pre>


## Resta de substitucions

|Cadena a substituir|Informació de la columna|Exemple|
|---|---|---|
|**```<nom de la vostra base de dades>```**|Nom de la base de dades|**```nieto-pardo```**|
|**```<usuari de connexió a la base de dades>```**|Usuari de connexió a la base de dades|**```nietopardo```**|
|**```<contrasenya usuari de la connexió>```**|Contrasenya de l'usuari de connexió|**```nietopardo123```**|

* **Comandes a executar**:

```
sudo sed -i 's/<nom de la vostra base de dades>/nieto-pardo/g' comandes-exemple.txt
sudo sed -i 's/<usuari de connexió a la base de dades>/nietopardo/g' comandes-exemple.txt
sudo sed -i 's/<contrasenya usuari de la connexió>/nietopardo123/g' comandes-exemple.txt
```


Executem una comanda per veure com ha quedat el contingut del fitxer **```comandes-exemple.txt```**. 

* **Comanda a executar**:

```
cat comandes-exemple.txt
```

* **Sortida**:

<pre>
sudo docker image list |grep php:7.0-fpm

sudo docker image list |grep nginx

sudo docker image list |grep mariadb

sudo docker pull php:7.0-fpm

sudo docker pull nginx

sudo docker pull mariadb

sudo mkdir ~/nieto-pardo

cd ~/nieto-pardo

sudo mkdir ~/nieto-pardo/webSrv

sudo vi ~/nieto-pardo/webSrv/Dockerfile

FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf

sudo vi ~/nieto-pardo/webSrv/default.conf

server {  

     listen 80 default_server;  
     root /var/www/html;  
     index index.html index.php;  

     charset utf-8;  

     location / {  
      try_files $uri $uri/ /index.php?$query_string;  
     }  

     location = /favicon.ico { access_log off; log_not_found off; }  
     location = /robots.txt { access_log off; log_not_found off; }  

     access_log off;  
     error_log /var/log/nginx/error.log error;  

     sendfile off;  

     client_max_body_size 100m;  

     location ~ .php$ {  
      fastcgi_split_path_info ^(.+.php)(/.+)$;  
      fastcgi_pass php:9000;  
      fastcgi_index index.php;  
      include fastcgi_params;
      fastcgi_read_timeout 300;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  
      fastcgi_intercept_errors off;  
      fastcgi_buffer_size 16k;  
      fastcgi_buffers 4 16k;  
    }  

     location ~ /.ht {  
      deny all;  
     }  
    }	
    
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/nieto-pardo/phpSrv/

sudo vi ~/nieto-pardo/phpSrv/Dockerfile

FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

sudo vi ~/nieto-pardo/docker-compose.yml

version: "3.9"
services:
   nginx:
     build: ./webSrv/
     ports:
       - 80:80
  
     volumes:
         - ./phpSrv/:/var/www/html/

   php:
     build: ./phpSrv/
     expose:
       - 9000
     volumes:
        - ./phpSrv/:/var/www/html/


   db:    
      image: mariadb  
      volumes: 
        -    mysql-data:/var/lib/mysql
      environment:  
       MYSQL_ROOT_PASSWORD: mariadb
       MYSQL_DATABASE: nieto-pardo 

volumes:
    mysql-data:
    
cd ~/nieto-pardo/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti nieto-pardo-db-1 bash

mariadb -u root -pmariadb

CREATE USER 'nietopardo'@'%' IDENTIFIED BY '<Contrasenya de l'usuari de connexió>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO 'nietopardo'@'%';

FLUSH PRIVILEGES;

show databases;

use nieto-pardo;

CREATE TABLE products(
  id mediumint(8) unsigned NOT NULL auto_increment,
  Name varchar(255) default NULL,
  Price varchar(255) default NULL,
  ImageUrl varchar(255) default NULL,
  PRIMARY KEY (id)
) AUTO_INCREMENT=1; 

INSERT INTO products (Name,Price,ImageUrl)
VALUES ("Laptop","100","c-1.png"),
       ("Drone","200","c-2.png"),
       ("VR","300","c-3.png"),
       ("Tablet","50","c-5.png"),
       ("Watch","90","c-6.png"),
       ("Phone Covers","20","c-7.png"),
       ("Phone","80","c-8.png"),
       ("Laptop","150","c-4.png");
       
exit

exit

cd ~/nieto-pardo/phpSrv

sudo vi index.php

$link = mysqli_connect('db', 'nietopardo', 'nietopardo123', 'nieto-pardo');
</pre>