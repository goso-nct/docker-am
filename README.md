# Learning docker from Artem's video
$ docker build -t hello-world .    
$ docker images  
$ docker run hello-world:latest  
$ docker ps -a  
$ docker rm de69aaf2bd26  
$ docker rm $(docker ps -qa)  

$ docker run --name hello -d hello-world

