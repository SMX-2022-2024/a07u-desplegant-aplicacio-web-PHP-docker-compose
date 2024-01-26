# a07u - Desplegant una aplicació web PHP amb Docker Compose, Nginx i MariaDB

Els grups han quedat de la següent manera:

|A |B
|--|--
|1<td rowspan="2">3</td>|2
|4|5
|6|7 

|Id|Alumne/a|Grup|Membres|Nom Base de dades|usuari|contrasenya
|:---|---|:---|:---:|:---|:---|:---
|7312|Agustí Corbella, Oriol<td rowspan="2">3Grup 01</td><td rowspan="2">42</td><td rowspan="2" colspan="5">5agusti-roman</td><td rowspan="2">6agustiroman</td><td rowspan="2">7agustiroman123</td>
|7422|Román Robles, Àlex



|7674|Boada Cirera, Jan|Grup 02|2|boada-cot|boadacot|boadacot123|
|7596|Cot Fontanella, Marc|Grup 02|2|boada-cot|boadacot|boadacot123|
|7582|Bollero Ruzafa, Ivan|Grup 03|2|bollero-pan|bolleropan|bolleropan123|
|7683|Pan , Jiahao|Grup 03|2|bollero-pan|bolleropan|bolleropan123|
|7572|Capel Vallbona, Marc|Grup 04|2|capel-codina|capelcodina|capelcodina123|
|7604|Codina Garcia, Aleix|Grup 04|2|capel-codina|capelcodina|capelcodina123|
|2708|Casas Lopez, Raul|Grup 05|2|casas-sardana|casassardana|casassardana123|
|7653|Sardaña Trinh, Marc|Grup 05|2|casas-sardana|casassardana|casassardana123|
|7579|Córdoba Xandri, Oriol|Grup 06|2|cordoba-puriy|cordobapuriy|cordobapuriy123|
|7659|Puriy Puriy, Nicolas|Grup 06|2|cordoba-puriy|cordobapuriy|cordobapuriy123|
|7636|Deus Jurado, Izan|Grup 07|2|deus-ortiz|deusortiz|deusortiz123|
|7576|Ortiz Guerrero, Antoni|Grup 07|2|deus-ortiz|deusortiz|deusortiz123|
|7627|Gálvez Comajuan, Marc|Grup 08|2|galvez-sohl|galvezsohl|galvezsohl123|
|7710|Sohl Brenes, Martin Albert|Grup 08|2|galvez-sohl|galvezsohl|galvezsohl123|
|7598|Garcia Fernández, Adrià|Grup 09|2|garcia-morales|garciamorales|garciamorales123|
|7473|Morales Gonzalez, Jan|Grup 09|2|garcia-morales|garciamorales|garciamorales123|
|7673|Garcia Romero, Arnau|Grup 10|2|garcia-royuela|garciaroyuela|garciaroyuela123|
|7799|Royuela Martín, Oriol|Grup 10|2|garcia-royuela|garciaroyuela|garciaroyuela123|
|7500|Lamela Garcia, Alvaro Haoan|Grup 11|2|lamela-soler|lamelasoler|lamelasoler123|
|7614|Soler Sampere, Arnau|Grup 11|2|lamela-soler|lamelasoler|lamelasoler123|
|7532|Martinez Segú, Eric|Grup 12|2|martinez-moreno|martinezmoreno|martinezmoreno123|
|7684|Moreno Fernández, Nil|Grup 12|2|martinez-moreno|martinezmoreno|martinezmoreno123|
|7260|Navarro Galan, Gerard|Grup 13|3|navarro-rueda-selles|navarroruedaselles|navarroruedaselles123|
|7668|Rueda Guàrdia, Marc|Grup 13|3|navarro-rueda-selles|navarroruedaselles|navarroruedaselles123|
|7459|Sellés Puyol, Aniol|Grup 13|3|navarro-rueda-selles|navarroruedaselles|navarroruedaselles123|
|7672|Pan , Le|Grup 14|2|pan-sacristan|pansacristan|pansacristan123|
|7836|Sacristan Castillo, Marc|Grup 14|2|pan-sacristan|pansacristan|pansacristan123|
|7581|Putellas Martín, Pol|Grup 15|2|putellas-vazquez|putellasvazquez|putellasvazquez123|
|7632|Vázquez Pelàez, Alex|Grup 15|2|putellas-vazquez|putellasvazquez|putellasvazquez123|

## Pas 1: Comprovació de que tenim descarregades les imatges.

* Comanda a executar:

```bash
sudo docker image list |grep php
sudo docker image list |grep nginx
sudo docker image list |grep mariadb
```

> Si no apareixen les imatges, llavors cal que les descarreguem:
>
> ```bash
> sudo docker pull php:7.0-fpm
> sudo docker pull nginx
> sudo docker pull mariadb
> ```

## Pas 2: Creació de la carpeta per ubicar el nostre sistema de contenidors.

El nom de la carpeta a on cal que ubiquem el nostre sistema de contenidors serà **```<CognomAlumne1>-<CognomAlumne2>```**.

On:
* **```<CognomAlumne1>```** és el **primer dels cognom** del **primer alumne** i
* **```<CognomAlumne2>```** és el **primer dels cognom** del **segon alumne**.

Com a ***primer*** i ***segon*** alumne s'enten l'ordre que queda una cop que els cognoms dels alumnes s'han ordenat alfabèticament.

Per exemple, en el cas de que els cognoms dels alumnes fossin, **Joan Pardo** i **Iván Nieto**, el nom de la carpeta seria **```nieto-pardo```**, ja que **Nieto** està en primera posició si ordenem els cognoms alfabeticament.


* Comanda a executar:

```bash
sudo mkdir ~/<CognomAlumne1>-<CognomAlumne2>
cd ~/<CognomAlumne1>-<CognomAlumne2>
```

Segons l'exemple:
<pre>
sudo mkdir ~/nieto-pardo
cd ~/nieto-pardo
</pre>

## Pas 3: Creació de la carpeta per ubicar la configuració i els fitxers pel contenidor ```web``` del nostre sistema de contenidors.

* Comanda a executar:

```bash
sudo mkdir ~/<CognomAlumne1>-<CognomAlumne2>/webSrv
```

* Segons l'exemple:

<pre>
sudo mkdir ~/nieto-pardo/webSrv
</pre>

## Pas 4: Creació del fitxer ```Dockerfile``` per la creació del contenidor ```web``` del nostre sistema de contenidors.

* Comanda a executar:

```bash
sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/webSrv/Dockerfile
```

* Segons l'exemple:

<pre>
sudo vi ~/nieto-pardo/webSrv/Dockerfile
</pre>

I el contingut del fitxer **```~/<CognomAlumne1>-<CognomAlumne2>/webSrv/Dockerfile```** és el següent:

```yml
FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf
```

## Pas 5: Creació del fitxer de configuració del fitxer ```default.conf``` per la configuració del contenidor ```web``` del nostre sistema de contenidors.

* Comanda a executar:

```bash
sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/webSrv/default.conf
```

* Segons l'exemple:

<pre>
sudo vi ~/nieto-pardo/webSrv/Dockerfile
</pre>

I el contingut del fitxer **```~/<CognomAlumne1>-<CognomAlumne2>/webSrv/default.conf```** és el següent:


```
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
```

## Pas 6: Descarrega d'una pàgina ja existent, escrita en ```php```, per mostrar informació.

```bash
sudo git clone https://github.com/rapidcode-technologies-private-limited/php-e-commerce.git ~/<CognomAlumne1>-<CognomAlumne2>/phpSrv/
```

## Pas 7: Creació del fitxer ***```Dockerfile```*** per la configuració del contenidor ```php``` del nostre sistema de contenidors.

```
sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/phpSrv/Dockerfile
```

I el contingut del fitxer **```~/<CognomAlumne1>-<CognomAlumne2>/phpSrv/Dockerfile```** és el següent:


```sql
FROM php:7.0-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli
```

```bash
sudo vi ~/<CognomAlumne1>-<CognomAlumne2>/docker-compose.yml
```

```yml
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
```

sudo docker exec -ti nieto-pardo-db-1 bash
mariadb -u root -pmariadb

```sql
CREATE USER 'nietopardo'@'%' IDENTIFIED BY "nietopardo123";

GRANT ALL PRIVILEGES ON *.* TO 'nietopardo'@'%';
FLUSH PRIVILEGES;

use nieto-pardo;

CREATE TABLE articles (
  id_article int(8) unsigned NOT NULL auto_increment,
  nom_article varchar(50) default NULL,
  preu_article decimal(4,2) default NULL,
  unitats_article smallint default NULL,
  PRIMARY KEY (id_article))
AUTO_INCREMENT=1; 

INSERT INTO articles (nom_article,preu_article,unitats_article)
VALUES  ("Aigua 5 litres",2.50,100); 
```