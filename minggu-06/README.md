# MINGGU 06   
# TUGAS PRATIKUM BIKIN LAPORAN BERDASARKAN LINK BERIKUT :

1. https://www.katacoda.com/courses/docker/deploying-first-container  
2. https://www.katacoda.com/courses/docker/create-nginx-static-web-server  
3. https://www.katacoda.com/courses/docker/2  


# Menjalankan Url No.1   
* Gambar 1  
![6](images/1..png) 
-- Pada gambar Menjalankan image redis menjadi container    
* Gambar 2  
![6](images/2.png) 
-- Pada gambar 2 ini untuk melihat container yang sedang berjalan  
* Gambar 3  
-- docker network create -d bridge roachnet
![6](images/3.png)
*  Gambar 4    
![6](images/4.png)   
* Gambar 5  
![6](images/5.png)  
* Gambar 6   
![6](images/6.png)   
* Gambar 7  
![6](images/7.png)   
* Gambar 8  
![6 ](images/8.png)   
* Gambar 9  
![6](images/9.png)  

# Menjalankan Url No.2  

1. Create Dockerfile  
* Membuat Dockerfile  
<pre>
FROM nginx:alpine
COPY . /usr/share/nginx/html
</pre>
![6](images/10.png)  
2. Build Docker Image  
Membuat image dari Dockerfile yang di buat sebelumnya  
<pre>
docker build -t webserver-image:v1 .
</pre> 
![6](images/11.png)  
3. Melihat/menampilkan isi dari images  
<pre>
docker images.
</pre>  
![6](images/12.png) 
4. Run  
* Menjalankan images menjadi sebuah container  
<pre>
docker run -d -p 80:80 webserver-image:v1  
</pre>  
![6](images/13.png)  
5. Membuka halaman docker dengan curl  
<pre>
curl docker
</pre> 
![6](images/14.png) 
















