# MINGGU 05  
# TUGAS PRATIKUM INSTALL DAN JALANKAN COCKROACH DATABSE

1. Install cockroach database  
* Jalankan Docker Quickstart Terminal  
![5](images/1.png)  
* Jalankan perintah docker pull cockroachdb/cockroach  
![5](images/2.PNG)  
2. Konfigurasi 
* Buat Bridge Network pada docker
-- docker network create -d bridge roachnet
![5](images/3.png)
* Jalankan service cockroachdb 
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
-- CREATE TABLE minggulima.accounts (id INT PRIMARY KEY, name VARCHAR, balance DECIMAL);
(yang dimana uuntuk nama tabel accounts di database minggulima)  
![5](images/10.png)  
  
5. Insert atau memasukan data kedalam tabel  
-- insert into minggulima.accounts VALUES (1, 'Lukman Surya Laksana', 10000.69);  
![5](images/11.png)
