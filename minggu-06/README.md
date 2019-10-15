# MINGGU 06   
# TUGAS PRATIKUM BIKIN LAPORAN BERDASARKAN LINK BERIKUT :

1. https://www.katacoda.com/courses/docker/deploying-first-container  
2. https://www.katacoda.com/courses/docker/create-nginx-static-web-server  
3. https://www.katacoda.com/courses/docker/2  


# Menjalankan Url No.1   
* Gambar 1  
![6](images/1..png)  
* Gambar 2  
![6](images/2.png)  
* Gambar 3  
-- docker network create -d bridge roachnet
![6](images/3.png)
*  Gambar 4
-- docker run -d --name=roach1 --hostname=roach1 --net=roachnet -p 26257:26257 -p 8080:8080 cockroachdb/cockroach start --insecure   
![5](images/4.png)   
* Cek container, pastikan UP  
-- docker ps -a  
![5](images/5.png)  
* Test Cluster  
-- docker exec -it roach1 ./cockroach sql --insecure  
![5](images/6.png)   
3. Create Databse dengan nama minggulima
-- create database minggulima; 
![5](images/7.png)   
* cek database  
-- show databases; 
![5](images/8.png)   
* menghubugkan databse/mengkonekkan  
-- use minggulima; 
![5](images/9.png)   

  
4. create Tabel   
  
5. Merubah lokasi dari branches02 ke branches master  

6. Vi Data   
   
7. Query Data  
) 