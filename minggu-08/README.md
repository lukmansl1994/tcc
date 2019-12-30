# MINGGU 08   
# PYTHON FT. FLASK 

* Sebelum melakukan Perintah di bawah ini silahkan Buat terlebih dahulu file-file pendukung, di dalam file tersebut terdapat beberapa perintah yag harus di isikan. untuk file pendukung tersebut silahkan masuk ke Folder FlaskApp

1. Jalankan Docker dan masuk ke root penyimpanan  
<pre>
PS C:\Users\Student> cd .\Documents\
PS C:\Users\Student\Documents> cd .\tcc\minggu-08\FlaskApp\
</pre>  
2. Membuat folder dasar untuk aplikasi Flask  
-- Step 1  
<pre>
PS C:\Users\Student\Documents\tcc\minggu-08\FlaskApp> mkdir -p app/static app/templates
mkdir : A positional parameter cannot be found that accepts argument 'app/templates'.
At line:1 char:1
+ mkdir -p app/static app/templates
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [mkdir], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,mkdir
</pre>  
-- Step 2  
<pre>
PS C:\Users\Student\Documents\tcc\minggu-08\FlaskApp> mkdir -p app/static
    Directory: C:\Users\Student\Documents\tcc\minggu-08\FlaskApp\app
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       11/19/2019   8:40 PM                static
</pre>  
-- Step 3  
<pre>
PS C:\Users\Student\Documents\tcc\minggu-08\FlaskApp> mkdir -p app/templates

    Directory: C:\Users\Student\Documents\tcc\minggu-08\FlaskApp\app

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       11/19/2019   8:40 PM                templates
</pre>  

# Setting Up Docker  

1. Buat Dockerfile, yang berisikan   
<pre>
FROM tiangolo/uwsgi-nginx-flask:python3.6-alpine3.7
RUN apk --update add bash nano
ENV STATIC_URL /static
ENV STATIC_PATH /var/www/app/static
COPY ./requirements.txt /var/www/requirements.txt
RUN pip install -r /var/www/requirements.txt
</pre> 
2. Build images docker with command `docker build -t lukmansl/python-flask:v1 .`  
<pre>
$ docker build -t lukmansl/python-flask:v1 .
Sending build context to Docker daemon  19.97kB
Step 1/6 : FROM tiangolo/uwsgi-nginx-flask:python3.6-alpine3.7
 ---> c902fcf59a97
Step 2/6 : RUN apk --update add bash nano
 ---> Using cache
 ---> b77a13c1c4c8
Step 3/6 : ENV STATIC_URL /static
 ---> Using cache
 ---> 768682fac3ef
Step 4/6 : ENV STATIC_PATH /var/www/app/static
 ---> Using cache
 ---> e44af29b3079
Step 5/6 : COPY ./requirements.txt /var/www/requirements.txt
 ---> Using cache
 ---> 7c6decb581f8
Step 6/6 : RUN pip install -r /var/www/requirements.txt
 ---> Using cache
 ---> 37c59c1d3ea1
Successfully built 37c59c1d3ea1
Successfully tagged lukmansl1994/python-flask:v1
SECURITY WARNING: You are building a Docker image from Windows against a non-Win
dows Docker host. All files and directories added to build context will have '-r
wxr-xr-x' permissions. It is recommended to double check and reset permissions f
or sensitive files and directories.
</pre> 
3. Cek image dengan perintah `docker images`  
<pre>
$ docker images
REPOSITORY                   TAG                   IMAGE ID            CREATED
           SIZE
docker.test                  latest                37c59c1d3ea1        11 minute
s ago      199MB
lukmansl1994/python-flask        v1                    37c59c1d3ea1        11 minute
s ago      199MB
drupal                       latest                115c57355190        3 weeks a
go         449MB
postgres                     10                    1ba73c5b23e7        3 weeks a
go         250MB
tiangolo/uwsgi-nginx-flask   python3.6-alpine3.7   c902fcf59a97        2 months
ago        189MB
</pre>  
4. jalankan perintah start.sh yang digunakan untuk menjalankan scrip docker build dan kemudian di run  
<pre>
$ ./start.sh
Sending build context to Docker daemon  14.34kB
Step 1/6 : FROM tiangolo/uwsgi-nginx-flask:python3.6-alpine3.7
python3.6-alpine3.7: Pulling from tiangolo/uwsgi-nginx-flask
48ecbb6b270e: Pull complete
692f29ee68fa: Pull complete
f75fc7ac1098: Pull complete
c30e40bb471c: Pull complete
51a8cc25b36b: Pull complete
6799a258469c: Pull complete
ff0cc983e766: Pull complete
643e5a6a19ec: Pull complete
51e17a22e825: Pull complete
651a730aa641: Pull complete
aa96895bf4f7: Pull complete
f9bd87bb8336: Pull complete
945b650f45fb: Pull complete
ac94e9dcce94: Pull complete
5ed3bad2a086: Pull complete
818c72442fb0: Pull complete
d8170b486028: Pull complete
4d935f5228ba: Pull complete
0b085d4bcdbd: Pull complete
830b3bff36db: Pull complete
Digest: sha256:96a27bf996c38965622a84bfba54cd22c7c9e29618b84923b16f20949999bf91
Status: Downloaded newer image for tiangolo/uwsgi-nginx-flask:python3.6-alpine3.7
 ---> c902fcf59a97
Step 2/6 : RUN apk --update add bash nano
 ---> Running in be7e8165db9c
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/community/x86_64/APKINDEX.tar.gz
(1/4) Installing pkgconf (1.3.10-r0)
(2/4) Installing bash (4.4.19-r1)
Executing bash-4.4.19-r1.post-install
(3/4) Installing libmagic (5.32-r2)
(4/4) Installing nano (2.9.1-r0)
Executing busybox-1.27.2-r11.trigger
OK: 135 MiB in 62 packages
Removing intermediate container be7e8165db9c
 ---> 8542d865f1ff
Step 3/6 : ENV STATIC_URL /static
 ---> Running in 34565ed00194
Removing intermediate container 34565ed00194
 ---> f6f80db41849
Step 4/6 : ENV STATIC_PATH /var/www/app/static
 ---> Running in 3a0a7d651c41
Removing intermediate container 3a0a7d651c41
 ---> 7d2bf981685e
Step 5/6 : COPY ./requirements.txt /var/www/requirements.txt
 ---> 5dcb74fe8a58
Step 6/6 : RUN pip install -r /var/www/requirements.txt
 ---> Running in 881ca8d6e477
Collecting Flask==1.0.2 (from -r /var/www/requirements.txt (line 1))
  Downloading https://files.pythonhosted.org/packages/7f/e7/08578774ed4536d3242b14dacb4696386634607af824ea997202cd0edb4b/Flask-1.0.2-py2.py3-none-any.whl (91kB)
Requirement already satisfied: click>=5.1 in /usr/local/lib/python3.6/site-packages (from Flask==1.0.2->-r /var/www/requirements.txt (line 1)) (7.0)
Requirement already satisfied: Jinja2>=2.10 in /usr/local/lib/python3.6/site-packages (from Flask==1.0.2->-r /var/www/requirements.txt (line 1)) (2.10.3)
Requirement already satisfied: itsdangerous>=0.24 in /usr/local/lib/python3.6/site-packages (from Flask==1.0.2->-r /var/www/requirements.txt (line 1)) (1.1.0)
Requirement already satisfied: Werkzeug>=0.14 in /usr/local/lib/python3.6/site-packages (from Flask==1.0.2->-r /var/www/requirements.txt (line 1)) (0.16.0)
Requirement already satisfied: MarkupSafe>=0.23 in /usr/local/lib/python3.6/site-packages (from Jinja2>=2.10->Flask==1.0.2->-r /var/www/requirements.txt (line 1)) (1.1.1)
Installing collected packages: Flask
  Found existing installation: Flask 1.1.1
    Uninstalling Flask-1.1.1:
      Successfully uninstalled Flask-1.1.1
Successfully installed Flask-1.0.2
You are using pip version 19.0.1, however version 19.3.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Removing intermediate container 881ca8d6e477
 ---> 35638d245317
Successfully built 35638d245317
Successfully tagged docker.test:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.
3bfdda2dd3b365ca3e3df0e52c0ade80e8153dde632c3fcb475332ab507ba286
</pre>  
5. jalankan perintah docker ps digunakan untuk melihat container yang berjalan  
<pre>
Student@DESKTOP-B8ACH4F MINGW64 ~/Documents/tcc/minggu-08/FlaskApp (master)
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                            NAMES
3bfdda2dd3b3        docker.test         "/entrypoint.sh /s..."   31 seconds ago      Up 31 seconds       443/tcp, 0.0.0.0:56733->80/tcp   docker.test
</pre>















