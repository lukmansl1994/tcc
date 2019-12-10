# MINGGU 12
# DInstall Drupal with Docker Compose  

1. Jalankan Docker terlebih dahulu kemudian masuk ke folder projeck anda   
2. Membuat folder dengan nama my-drupal  
<pre>
Student@DESKTOP-B8ACH4F MINGW64 ~/Documents/tcc/minggu-12 (master)
$ mkdir my_drupal
</pre>
3. Masuk ke root folder yang di buat  
<pre>  
Student@DESKTOP-B8ACH4F MINGW64 ~/Documents/tcc/minggu-12 (master)
$ cd
my_drupal/ README.md

Student@DESKTOP-B8ACH4F MINGW64 ~/Documents/tcc/minggu-12 (master)
$ cd my_drupal
</pre>  
4. Buat File dengan nama docker-compose.yml dan isikan script berikut  
<pre>
version: '3.3'

services:
  drupal:
    image: drupal:latest
    ports:
      - 80:80
    volumes:
      - drupal_modules:/var/www/html/modules
      - drupal_profiles:/var/www/html/profiles
      - drupal_themes:/var/www/html/themes
      - drupal_sites:/var/www/html/sites
    restart: always

  postgres:
    image: postgres:10
    environment:
      POSTGRES_PASSWORD: your_postgres_password
    volumes:
        - db_data:/var/lib/postgresql/data
    restart: always

volumes:
  drupal_modules:
  drupal_profiles:
  drupal_themes:
  drupal_sites:
  db_data:
</pre>   
5. Jalankan Docker compose dengan perintah  
<pre>
docker-compose up -d
</pre>    
- -d artinya di jalankan di belakang background  
6. 





















