##WAZIUP containers images overview
This repository contains three main directories that correspond to three main containers (**broker**,**database** and **web server**) that will run in WAZIUP cloud.
* The repository **Platform/broker/WAZIUPKafka/** contains the Dockerfile and scripts to build an environment based on [Apache Kafka](http://kafka.apache.org/). It help to create brokers and topics
* The repository **Platform/broker/WAZIUPDatabase/** contains the Dockerfile to build an [MongoDB](https://www.mongodb.com/) container that will host the WZAIUP big data nosql based database system.
* The repository **Platform/broker/WAZIUPWildfly/** contains the  Dockerfile to build a web server container based on JBOSS community version ; [wildfly](https://www.mongodb.com/). It will help to host application based on JavaEE and/or other frameworks.
</br>
</br>
![Image of containers and their orchestration](https://github.com/Waziup/Platform/blob/master/broker/doc/images/container.png)


##Prerequisites to use in local 
You need to have installed  [Docker](https://docs.docker.com/)  and [docker-compose](https://docs.docker.com/compose/install/) in your local computer. </br>
On Linux based machines here the link on how to install it  : [Docker installation on Linux](https://docs.docker.com/engine/installation/linux/). </br>
If you are on a Windows or Mac it is recommanded to install the all-in-one tool [Docker Toolbox](https://docs.docker.com/toolbox/overview/).

##Running the docker images  - Individually or using docker-compose
The platform offer the possibility to run indeividually the docker images  and using docker-compose as well. 
</br>
* Run each docker image individually
  1. Download the docker images from [WAZIUP platform](https://github.com/Waziup/Platform.git) github repository.
  2. Build the docker images 
</br>
  `cd  Platform/broker/WAZIUPKafka`
</br>
  ```$ docker build -t <image name>  .``` where **image name** is the name of the container image.
</br> 
  For example  `$ docker build -t  waziupkafka .`.Do not forget the dot at the end of the command !</br>
  `cd Platform/broker/WAZIUPDatabase`
</br>
  `$ docker build -t waziupmongodb .`
</br>
  `cd Platform/broker/WAZIUPWildfly`
</br>
  `$ docker build -t waziupwildfly .`
</br>
List the images built with the command `$ docker images`. The result should be like the picture below : 
</br>
![Images list](https://github.com/Waziup/Platform/blob/master/broker/doc/images/dockerimage.png)
 3. Run the images </br>
  `$ docker run -it <image name> `where **image name** is the name of container image.
</br>
  `$ docker run -it waziupkafka`
</br>
  `$ docker run -it waziupmongodb`
</br>
  `$ docker run -it waziupwildfly`
</br>
List of running containers with the command `$ docker ps -a`. The result should show the picture below :
</br>
![Containers running](https://github.com/Waziup/Platform/blob/master/broker/doc/images/runningcontainer.png)
</br> Usefull commands : 
List the IP address of a container : </br>
`$ docker inspect --format '{{ .NetworkSettings.IPAddress }}' <Container_ID>`
</br>
Remove container </br>
`$ docker rm <Container ID>` 

* Run all docker images all at once with docker-compose </br>
Rather executing the images one by one , you can run all of them at once thank to docker-composer. Then you only need to download the file  **docker-compose.yml**  in repository  **Plaform/broker**.</br>
Go to the directory where you download the docker-compose.yml and execute the command below:</br>
`$ docker-compose up `
</br>
Here the screenshot of probable result of the command :
</br>
![image docker-compose command](https://github.com/Waziup/Platform/blob/master/broker/doc/images/compose.png)

## Containers ready ! How to use resources ? 
:one: **Use the brokers container** </br>
You can connect to the container by executing the command : </br>
`$ docker exec -it <Container ID> bash` where **Container ID** is the broker container identifier(can be found in the result of the command `docker ps -a` . It corresponds to the first column).
</br>
For example we have `$ docker exec -it c3d56b284447 bash`  </br>
Once you have the shell prompt, execute the  `listtopic` that will show the topics created. Whenever the result is empty that means you have no topic created. You have choice between two commands for this purpose : **createdefaulttopic** and **createtopic** . </br>
* **createdefaulttopic** will create one default topic name **waziupfarmingtopic** </br>
* **createtopic** will create a topic that name has been provided at prompt </br>
</br>
The `createdefaulttopic` command gives this : </br>
</br>
![create default topic](https://github.com/Waziup/Platform/blob/master/broker/doc/images/createdefaulttopic.png) </br>
The `createtopic` command gives this : </br>
</br>
![create a topic](https://github.com/Waziup/Platform/blob/master/broker/doc/images/createtopic.png) </br>




:two: **Use database container** </br>



:three: **Use web server container** </br>
