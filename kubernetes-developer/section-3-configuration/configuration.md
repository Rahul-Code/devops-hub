### configuration  

containerize the application: How do create own docker image  
1) write the steps  
2) create docker file
3) run docker build command & docker push command to build and push image to dockerhub

example:  
1. OS-ubantu  
2. update apt repo  
3. install dependenies using apt repo  
4. install pythin dep using pip  
5. copy source code to /opt folder
6. run the web server using flask command  


docker file  

FROM Ubantu  

RUN api-get update   
RUN api-get install python  
RUN pip install flask  
RUN pip install flask-mysql  

COPY . /opt/source-code  

ENTRYPOINT FLASK_APP= /opt/source-code/app.py flask run 

docker build DockerFile -t c/dockerimages/my-app
docker push c/dockerimages/my-app --> docker registery  

Notes:  
 Docker will create the containers by using images built with Dockerfile.  
 what is HOST Port & Container Port


#### Commands in docker  

  Conatiners are mean for running some task and exist once it done. container will not just create os and run without running any PID(process), each task consider as PID.  
  container will live until pid is up and running.  

  docker run ubabtu --> it will pull the latest image from docker and create container and run the os but it will not up & running all time because there is no pid attached.  

  docker images -a will show the all the images.  

  how do define to run task in container ?  or start the container.

  CMD argument:  `CMD ["nginx"]` --> contianer will start nginx once it created.  

  `CMD command param1` || `CMD ["command", "param1"]`   
for example CMD["sleep", "5"]  

 This is hardcoded value in docker file but how we can override this value.  
 `docker run ubantu sleep 10`  --> it will override values in docker image.  
 do not want to mention sleep in docker run arg so `ENTRYPOINT` will come into picture  

 `ENTRYPOINT ["sleep"]` --> mentioning commange name  and expecting values from arguments.  
 we can use `CMD & ENTRYPOINT together` to have the default values for command arg so that container will take default values if user did not mention in docker run command.  
`ENTRYPOINT ["sleep"]`  
`CMD ["5"]`
`docker run ubuntu 10` --> it wwnt sleep mode for 10 sec  
`docker run ubantu` --> contianer will sleep dafult 5 sec from CMD values  

`docker run ubantu --entrypoint `  

#### Commands in kuberneties:  







