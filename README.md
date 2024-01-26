# a07u - Desplegant una aplicació web PHP amb Docker Compose, Nginx i MariaDB

Els grups han quedat de la següent manera:
<table>
  <tr>
    <th rowspan="3">Id</th>
    <th rowspan="3">Alumne/a</th>
    <th rowspan="3">Grup</th>
    <th colspan="3">De la base de dades</th>
  </tr>
  <tr>
    <th rowspan="2">Nom</th>
    <th rowspan="2">Usuari</th>
    <th rowspan="2">contrasenya</th>
  </tr>
  <tr></tr>
  <tr>
    <td>7312</td><td>Agustí Corbella, Oriol</td><td rowspan="2">Grup&nbsp;01</td><td rowspan="2">agusti-roman</td><td rowspan="2">agustiroman</td><td rowspan="2">agustiroman123</td>
  </tr>
  <tr>
  <td>7422</td><td>Román Robles, Àlex</td>
</tr>
<tr><td>7674</td><td>Boada Cirera, Jan</td><td rowspan="2">Grup&nbsp;02</td><td rowspan="2">boada-cot</td><td rowspan="2">boadacot</td><td rowspan="2">boadacot123</td></tr>
<tr><td>7596</td><td>Cot Fontanella, Marc</td></tr>
<tr><td>7582</td><td>Bollero Ruzafa, Ivan</td><td rowspan="2">Grup&nbsp;03</td><td rowspan="2">bollero-pan</td><td rowspan="2">bolleropan</td><td rowspan="2">bolleropan123</td></tr>
<tr><td>7683</td><td>Pan , Jiahao</td></tr>
<tr><td>7572</td><td>Capel Vallbona, Marc</td><td rowspan="2">Grup&nbsp;04</td><td rowspan="2">capel-codina</td><td rowspan="2">capelcodina</td><td rowspan="2">capelcodina123</td></tr>
<tr><td>7604</td><td>Codina Garcia, Aleix</td></tr>
<tr><td>2708</td><td>Casas Lopez, Raul</td><td rowspan="2">Grup&nbsp;05</td><td rowspan="2">casas-sardana</td><td rowspan="2">casassardana</td><td rowspan="2">casassardana123</td></tr>
<tr><td>7653</td><td>Sardaña Trinh, Marc</td></tr>
<tr><td>7579</td><td>Córdoba Xandri, Oriol</td><td rowspan="2">Grup&nbsp;06</td><td rowspan="2">cordoba-puriy</td><td rowspan="2">cordobapuriy</td><td rowspan="2">cordobapuriy123</td></tr>
<tr><td>7659</td><td>Puriy Puriy, Nicolas</td></tr>
<tr><td>7636</td><td>Deus Jurado, Izan</td><td rowspan="2">Grup&nbsp;07</td><td rowspan="2">deus-ortiz</td><td rowspan="2">deusortiz</td><td rowspan="2">deusortiz123</td></tr>
<tr><td>7576</td><td>Ortiz Guerrero, Antoni</td></tr>
<tr><td>7627</td><td>Gálvez Comajuan, Marc</td><td rowspan="2">Grup&nbsp;08</td><td rowspan="2">galvez-sohl</td><td rowspan="2">galvezsohl</td><td rowspan="2">galvezsohl123</td></tr>
<tr><td>7710</td><td>Sohl Brenes, Martin Albert</td></tr>
<tr><td>7598</td><td>Garcia Fernández, Adrià</td><td rowspan="2">Grup&nbsp;09</td><td rowspan="2">garcia-morales</td><td rowspan="2">garciamorales</td><td rowspan="2">garciamorales123</td></tr>
<tr><td>7473</td><td>Morales Gonzalez, Jan</td></tr>
<tr><td>7673</td><td>Garcia Romero, Arnau</td><td rowspan="2">Grup&nbsp;10</td><td rowspan="2">garcia-royuela</td><td rowspan="2">garciaroyuela</td><td rowspan="2">garciaroyuela123</td></tr>
<tr><td>7799</td><td>Royuela Martín, Oriol</td></tr>
<tr><td>7500</td><td>Lamela Garcia, Alvaro Haoan</td><td rowspan="2">Grup&nbsp;11</td><td rowspan="2">lamela-soler</td><td rowspan="2">lamelasoler</td><td rowspan="2">lamelasoler123</td></tr>
<tr><td>7614</td><td>Soler Sampere, Arnau</td></tr>
<tr><td>7532</td><td>Martinez Segú, Eric</td><td rowspan="2">Grup&nbsp;12</td><td rowspan="2">martinez-moreno</td><td rowspan="2">martinezmoreno</td><td rowspan="2">martinezmoreno123</td></tr>
<tr><td>7684</td><td>Moreno Fernández, Nil</td></tr>
<tr><td>7260</td><td>Navarro Galan, Gerard</td><td rowspan="3">Grup&nbsp;15</td><td rowspan="3">navarro-rueda-selles</td><td rowspan="3">navarroruedaselles</td><td rowspan="3">navarroruedaselles123</td></tr>
<tr><td>7668</td><td>Rueda Guàrdia, Marc</td></tr>
<tr><td>7459</td><td>Sellés Puyol, Aniol</td></tr>
<tr><td>7672</td><td>Pan , Le</td><td rowspan="2">Grup&nbsp;13</td><td rowspan="2">pan-sacristan</td><td rowspan="2">pansacristan</td><td rowspan="2">pansacristan123</td></tr>
<tr><td>7836</td><td>Sacristan Castillo, Marc</td></tr>
<tr><td>7581</td><td>Putellas Martín, Pol</td><td rowspan="2">Grup&nbsp;14</td><td rowspan="2">putellas-vazquez</td><td rowspan="2">putellasvazquez</td><td rowspan="2">putellasvazquez123</td></tr>
<tr><td>7632</td><td>Vázquez Pelàez, Alex</td></tr>
</table>

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