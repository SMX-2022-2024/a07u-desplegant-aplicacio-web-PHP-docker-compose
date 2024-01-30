# **TOTES** les comandes per fer l'activitat

En el fitxer d'aquest repositori teniu el fitxer [**```comandes.txt```**](./comandes.txt) que conté **TOTES** les comandes necessaries per fer l'activitat.

Les comandes apareixen amb un seguit de cadenes de text genèriques, de manera que es poden substituir amb els valors que hi ha la [taula dels grups](./README.md#taula-dels-grups) que apareix a l'inici de l'activitat.

A la columna **Exemple**, apareix una cadena de text, que es farà servir com  exemple per poder explicar com cal fer les substitucions.

Us recordo que de les cadenes de text a substituir **sempre cal incloure** els caracters **```<```** **```>```**, ja que apareixen com a **delimitadors** de les cadenes de text genèriques.

A continuació es facilita una relació les cadenes de text genèriques i com es poden substituir.

|Cadena a substituir|Nom de la columna de la taula|Vegades que<br>apareix|Exemple|
|---|---|:---:|---|
|**```<CognomAlumne1>-<CognomAlumne2>```**|Nom de la base de dades|**11**|**```bellavista-nieto```**|
|**```<nom-de-la-vostra-base-de-dades>```**|Nom de la base de dades|**3**|**```bellavista-nieto```**|
|**```<usuari-de-connexio-a-la-base-de-dades>```**|Usuari de connexió a la base de dades|**3**|**```bellavistanieto```**|
|**```<contrasenya-de-l-usuari-de-la-connexio>```**|Contrasenya de l'usuari de connexió|**1**|**```bellavistanieto123```**|

Un cop fet aquestes substitucions, si ho heu fet bé, tindreu totes les comandes que cal que executeu per fer la vostra activitat.

La comanda que es farà servir és **```sed```** (***stream editor*** -> **editor de flux**). Es tracta d'un editor de text de línia d'ordres no interactiu.

```
sudo sed -i 's/Cadena a substituir/Informació de la columna/g' comandes-exemple.txt
```

Exemple de comandes per fer les substitucions.

<details><summary>Pitja per veure el contingut del fitxer comandes-exemple.txt</summary>

Executem una comanda previa per veure el contingut del fitxer **```comandes-exemple.txt```**. 

* **Comanda a executar**:

```
cat comandes-exemple.txt
```

* **Sortida**:

```bash

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
       MYSQL_DATABASE: <nom-de-la-vostra-base-de-dades> 

volumes:
    mysql-data:
    
cd ~/<CognomAlumne1>-<CognomAlumne2>/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti <CognomAlumne1>-<CognomAlumne2>-db-1 bash

mariadb -u root -pmariadb

CREATE USER '<usuari-de-connexio-a-la-base-de-dades>'@'%' IDENTIFIED BY '<contrasenya-de-l-usuari-de-la-connexio>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO '<usuari-de-connexio-a-la-base-de-dades>'@'%';

FLUSH PRIVILEGES;

show databases;

use <nom-de-la-vostra-base-de-dades>;

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

$link = mysqli_connect('db', '<usuari-de-connexio-a-la-base-de-dades>', '<contrasenya-de-l-usuari-de-la-connexio>', '<nom-de-la-vostra-base-de-dades>');
```
<hr>
</details>

## Primera substitució

|Cadena a substituir|Informació de la columna|Exemple|
|---|---|---|
|**```<CognomAlumne1>-<CognomAlumne2>```**|Nom de la base de dades|**```bellavista-nieto```**|

* **Comanda a executar**:

```
sudo sed -i 's/<CognomAlumne1>-<CognomAlumne2>/bellavista-nieto/g' comandes-exemple.txt
```

<details><summary>Pitja per veure el contingut del fitxer comandes-exemple.txt desprès de l'execució de la primera de les comandes.</summary>
<hr>

```bash
sudo docker image list |grep php:7.0-fpm

sudo docker image list |grep nginx

sudo docker image list |grep mariadb

sudo docker pull php:7.0-fpm

sudo docker pull nginx

sudo docker pull mariadb

sudo mkdir ~/bellavista-nieto

cd ~/bellavista-nieto

sudo mkdir ~/bellavista-nieto/webSrv

sudo vi ~/bellavista-nieto/webSrv/Dockerfile

FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf

sudo vi ~/bellavista-nieto/webSrv/default.conf

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
    
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/bellavista-nieto/phpSrv/

sudo vi ~/bellavista-nieto/phpSrv/Dockerfile

FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

sudo vi ~/bellavista-nieto/docker-compose.yml

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
       MYSQL_DATABASE: <nom-de-la-vostra-base-de-dades> 

volumes:
    mysql-data:
    
cd ~/bellavista-nieto/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti bellavista-nieto-db-1 bash

mariadb -u root -pmariadb

CREATE USER '<usuari-de-connexio-a-la-base-de-dades>'@'%' IDENTIFIED BY '<contrasenya-de-l-usuari-de-la-connexio>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO '<usuari-de-connexio-a-la-base-de-dades>'@'%';

FLUSH PRIVILEGES;

show databases;

use <nom-de-la-vostra-base-de-dades>;

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

cd ~/bellavista-nieto/phpSrv

sudo vi index.php

$link = mysqli_connect('db', '<usuari-de-connexio-a-la-base-de-dades>', '<contrasenya-de-l-usuari-de-la-connexio>', '<nom-de-la-vostra-base-de-dades>');
```
<hr>
</details>


## Resta de substitucions

|Cadena a substituir|Informació de la columna|Exemple|
|---|---|---|
|**```<nom-de-la-vostra-base-de-dades>```**|Nom de la base de dades|**```bellavista-nieto```**|
|**```<usuari-de-connexio-a-la-base-de-dades>```**|Usuari de connexió a la base de dades|**```bellavistanieto```**|
|**```<contrasenya usuari de la connexió>```**|Contrasenya de l'usuari de connexió|**```bellavistanieto123```**|

* **Comandes a executar**:

```
sudo sed -i 's/<nom-de-la-vostra-base-de-dades>/bellavista-nieto/g' comandes-exemple.txt
sudo sed -i 's/<usuari-de-connexio-a-la-base-de-dades>/bellavistanieto/g' comandes-exemple.txt
sudo sed -i 's/<contrasenya usuari de la connexió>/bellavistanieto123/g' comandes-exemple.txt
```

<details><summary>Pitja per veure el contingut del fitxer comandes-exemple.txt desprès de l'execució de les comandes.</summary>

Executem una comanda per veure com ha quedat el contingut del fitxer **```comandes-exemple.txt```**. 

* **Comanda a executar**:

```
cat comandes-exemple.txt
```

* **Sortida**:


```bash
sudo docker image list |grep php:7.0-fpm

sudo docker image list |grep nginx

sudo docker image list |grep mariadb

sudo docker pull php:7.0-fpm

sudo docker pull nginx

sudo docker pull mariadb

sudo mkdir ~/bellavista-nieto

cd ~/bellavista-nieto

sudo mkdir ~/bellavista-nieto/webSrv

sudo vi ~/bellavista-nieto/webSrv/Dockerfile

FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf

sudo vi ~/bellavista-nieto/webSrv/default.conf

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
    
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/bellavista-nieto/phpSrv/

sudo vi ~/bellavista-nieto/phpSrv/Dockerfile

FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

sudo vi ~/bellavista-nieto/docker-compose.yml

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
       MYSQL_DATABASE: bellavista-nieto 

volumes:
    mysql-data:
    
cd ~/bellavista-nieto/
sudo docker compose up -d

sudo docker container list -a | grep db-1

sudo docker exec -ti bellavista-nieto-db-1 bash

mariadb -u root -pmariadb

CREATE USER 'bellavistanieto'@'%' IDENTIFIED BY '<contrasenya-de-l-usuari-de-la-connexio>';

SELECT user FROM mysql.user;

GRANT ALL PRIVILEGES ON *.* TO 'bellavistanieto'@'%';

FLUSH PRIVILEGES;

show databases;

use bellavista-nieto;

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

cd ~/bellavista-nieto/phpSrv

sudo vi index.php

$link = mysqli_connect('db', 'bellavistanieto', 'bellavistanieto123', 'bellavista-nieto');
```
<hr>
</details>
