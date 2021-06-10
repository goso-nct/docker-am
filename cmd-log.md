#ver 1  
```
print("Hello, World !")
```

Создаём имадж для приложения:  
(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker build -t hello-world .**  
```
Sending build context to Docker daemon  13.84MB
Step 1/5 : FROM python:3.8
3.8: Pulling from library/python
d960726af2be: Pulling fs layer 
...
a181a2736d7a: Pull complete 
Digest: sha256:a1563de7f9c8c47357637a646bc14eef26a16512ec7133c36e3f186a466aba7b
Status: Downloaded newer image for python:3.8
 ---> e7d3be492e61
Step 2/5 : RUN mkdir -p /usr/src/app/
 ---> Running in 330cc99ffd5d
Removing intermediate container 330cc99ffd5d
 ---> 5ebcd8ee4002
Step 3/5 : WORKDIR /usr/src/app/
 ---> Running in 2fc66984b07d
Removing intermediate container 2fc66984b07d
 ---> ab46b95e2a4b
Step 4/5 : COPY . /usr/src/app/
 ---> 7c4668f8a9a6
Step 5/5 : CMD ["python", "app.py"]
 ---> Running in b75d30d414dc
Removing intermediate container b75d30d414dc
 ---> 4752cbc47225
Successfully built 4752cbc47225
Successfully tagged hello-world:latest
```

(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker images**
```
REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
hello-world   latest    4752cbc47225   18 minutes ago   896MB
python        3.8       e7d3be492e61   2 weeks ago      883MB
hello-world   <none>    d1165f221234   3 months ago     13.3kB
```
(нижний hello это тест докера)  

Запускаем:  
(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker run hello-world:latest**
```
Hello, World !
```

Смотрим контейнеры:  
(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker ps -a**
```
CONTAINER ID   IMAGE                COMMAND           CREATED             STATUS                         PORTS     NAMES
0325ec4e10ec   d1165f221234         "/hello"          32 minutes ago      Exited (0) 32 minutes ago                affectionate_proskuriakova
27ff7f73a89b   hello-world          "python app.py"   33 minutes ago      Exited (0) 33 minutes ago                infallible_shannon
eee6f9a9b057   hello-world:latest   "python app.py"   34 minutes ago      Exited (0) 34 minutes ago                objective_bhaskara
de69aaf2bd26   d1165f221234         "/hello"          About an hour ago   Exited (0) About an hour ago             great_moser
```

Удаляем контейнер:  
(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker rm de69aaf2bd26**
```
de69aaf2bd26
```
Удаляем контейнеры:  
(venv) vg@ubu20box:~/PycharmProjects/docker$ **docker rm $(docker ps -qa)**
```
0325ec4e10ec
27ff7f73a89b
```

#ver 2  
```
while True:  
  print("Hello, World !")  
  time.sleep(1)  
```

vg@ubu20box:~/PycharmProjects/docker-am$ **docker build -t hello-world .**  
```
Sending build context to Docker daemon  13.91MB  
Step 1/5 : FROM python:3.8  
 ---> e7d3be492e61  
Step 2/5 : RUN mkdir -p /usr/src/app/  
 ---> **Using cache**  
 ---> 5ebcd8ee4002  
...  
Successfully tagged hello-world:latest
```

vg@ubu20box:~/PycharmProjects/docker-am$ **docker run --name hello -d hello-world**
```
ebc017befa6441609400d3458a10058a13147581d02db6561d07b9ea28c357de
```

vg@ubu20box:~/PycharmProjects/docker-am$ **docker ps**
```
CONTAINER ID   IMAGE         COMMAND           CREATED          STATUS         PORTS     NAMES
ebc017befa64   hello-world   "python app.py"   11 seconds ago   Up 9 seconds             hello
```

vg@ubu20box:~/PycharmProjects/docker-am$ **docker stop hello**  
```
hello
```

vg@ubu20box:~/PycharmProjects/docker-am$ **docker ps -a**
```
CONTAINER ID   IMAGE         COMMAND           CREATED         STATUS                        PORTS     NAMES
ebc017befa64   hello-world   "python app.py"   4 minutes ago   Exited (137) 30 seconds ago             hello
```
_Status 137_ т.к. погасили стопом  

Для автоматического удаления контейнера после его отработки:  
docker run --name hello -d **-rm** hello-world



