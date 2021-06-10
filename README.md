# Learning docker from Artem's video
$ docker **build** -t hello-world .    
$ docker **images**  
$ docker **run** hello-world:latest  
$ docker **ps**  
$ docker **ps -a**  
$ docker **rm** de69aaf2bd26  
$ docker rm **$(docker ps -qa)**  
$ docker **run** --name hello -d hello-world  
$ docker **stop** hello  
$ docker run --name hello -d **--rm** hello-world  

pip install -r requirements.txt

EXPOSE 8080  
ENV TZ=Europe/Moscow
  
$ docker run --rm --name web **-p 8080:8080** web-hello  
$ docker run --rm --name web -p 8080:8080 **-e TZ=Europe/Moscow** web-hello  



