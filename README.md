# Docker  

1. docker pull  `<imageName>` ->pull image from docker registry or local if available 

2. docker run `<imageName>`  -> run the image 

3. docker run -p 8085:8085 `<imagename>` 

4. docker run -d -p 8080:8081 `<imageName>` --> d-detachmode p-publish on 8080-HostPort,8081-Containerport 

5. docker ps --> list all the running container 

6. docker ps -a -->list all the available containers 

7. docker rm container name/id --> remove the container 

8. docker ps -aq -->display  all the containers id 

9. docker rm $(docker ps -aq) -->Remove all the containers 

10. docker stop container id/name -->stop the container 

11. docker run -name/-n  `<container name>` -d -p 8081:8080 `<imageName>` // -name - to define container name 

12. docker build -f DockerFile --tag/-t `<ImageName >` . -->build - build the image, f- file ,tag-for defining image name, . -current directory 

13. docker container prune -->stop all the running containers 

14. docker container pause  id/name -->pause the container with the id/name 

15. docker container unpause id/name -->unpause the container with the id/name 

16. docker image remove id/name --> delete the image with name/id 

17. docker compose up -->to run the docker compose 

 

18. "C:\Program Files\Docker\Docker\DockerCli.exe" -SwitchDaemon  -->To enable docker to start automatically after our system restarts 

 

 

 

                      Docker Swarm 

19. docker swarm init -–advertise-addr `<manager-ip>` -->used to initialize a swarm with manager 

20. docker info -->to get the information about the swarm 

21. docker node ls -->gives list of connected nodes 

22. docker swarm leave (or) docker swarm leave –force // this command is used from the node terminal to leave the swarm 

23. docker node rm `<node-id>` (or) docker node rm -f `<node-id>` // this command is used from the manager node terminal to remove the worker node 

24. docker swarm join-token worker -->to join a new worker node from manager node terminal (i.e. it will generate a token) 

25. docker service create –name `<service name>` –replicas `<number-of-replicas> -p <port-mapping> <image-name>` -->to create a new service. 

26. docker service ls -->to list all the service 

27. docker service rm id/name -->to remove the service  

28. docker service inspect –pretty id/name -->to inspect a service 

29. docker service ps id/name -->to list all the nodes the running the service  

 

Scaling 

 

    docker service scale id/name=’no of replicas we want     to  scale’ //to scale the service 

 

Rolling updates 

 

    docker service update –image <new image> <old image> // used to update an image in the service while being it is run. 

 

Draining Nodes 

      

    docker node update –availability drain worker1 //drain status prevents the nodes from receiving tasks 

 

Connecting to a network 

       

     docker network create –driver overlay <network name> //this command is used to create an overlay network 

      docker service create –replicas 3 –network <network name> --name <service name> <image> // to start a service with an overlay network 

      docker service update –network-add <network name> <service name> // to add network to an existing service 

      docker service update –network-rm <network name> <service name> // to remove a network  

 

  # Giving Storage Access 

  1. Volumes docker service create -–mount `src=<volume-name>,dst=<container-path> --name <service name> <image>` 

  2. Bind Mount docker service create –mount type=bind,`src=<host-path>,dst=<container-path> --name <servicename> <image>` 

   

 

17.  Replicated or Global services 

    1. docker service create –-name `<servicename>` --replicas 3 `<imagename>`//the tasks are replicated and assigned to each node 

    2. docker service create –-name `<servicename>` --mode global `<imagename>` //this run one tasks on every node 

 

18. –-reserve-memory (or) -–reserve-cpu -->flags can be used to reserve a certain amount of memory or number of CPUs for a service 

19. -–constraint -->flag can be used to allocate service tasks to only nodes with certain label value 

20. --placement-pref -->flag is used to evenly distribute the service tasks across nodes with certain label value 

