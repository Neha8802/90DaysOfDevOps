Task 1: What is Docker?

1. What is a container and why do we need them?
   Container is a linux process that runs the application we need them

   we need it because
   It solves "itsworking on my machine"
   its lightweight
   it takes less time to start
   own resources

2. Containers vs Virtual Machines — what's the real difference?
   Containers
   Its lighweight
   Its uses shared resoouces
   Docker Engine have direct access to kernel
   no duplication of os
   takes seconds to start

   Virtual Machines
   Its bulky
   Its uses half of resoources
   duplication of os
   takes minutes to start

Dockerclient - it is a commamd line tool you run your command into

image - image is a blueprint that is use to create the container

Container - contaienr is a linux process in which our applications run. It has is own resouces networs,
code, liberaries, depencies the only thing it takes from host is os.

Docker Registry - stores images like nginx, ubuntu.


3. What is the Docker architecture? (daemon, client, images, containers, registry)

   DockerDemom is also known as a dockerd its the backeknd process it basiclally takes the
   commands from docker client and then sends its to github or docerclient and provides
   the output.
   uns as a background process on your machine.

Receives commands from the Docker client.

Manages:

Images

Containers

Networks

Volumes

Downloads images from Docker Hub (or other registries) if needed.

Runs containers and returns results to the client.




Task 2: Install Docker
Run the hello-world container
<img width="558" height="309" alt="image" src="https://github.com/user-attachments/assets/dc18e09b-738d-4a8b-af38-609361de7385" />

Task 3: Run Real Containers
Run an Nginx container and access it in your browser

CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
54ddd2c51ccd   nginx     "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   funny_payne


<img width="934" height="49" alt="image" src="https://github.com/user-attachments/assets/33e39677-ef81-43fe-b67d-d74de8d03a87" />


<img width="1249" height="400" alt="image" src="https://github.com/user-attachments/assets/43b5a1d4-9771-4584-b837-7a1c02dc9279" />



Run an Ubuntu container in interactive mode — explore it like a mini Linux machine

<img width="796" height="375" alt="image" src="https://github.com/user-attachments/assets/63e1ec2b-fa5b-42fc-8e32-3672aa50413e" />

List all running containers

ubuntu@ip-172-31-23-28:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
9044a7f8bd7e   ubuntu    "/bin/bash"              6 minutes ago    Up 6 minutes                                          friendly_banzai
54ddd2c51ccd   nginx     "/docker-entrypoint.…"   25 minutes ago   Up 25 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   funny_payne

List all containers (including stopped ones)

ubuntu@ip-172-31-23-28:~$ docker ps -a
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
be602ee16b94   ubuntu             "/bin/bash"              6 minutes ago    Exited (0) 33 seconds ago                                         nostalgic_rubin
9044a7f8bd7e   ubuntu             "/bin/bash"              7 minutes ago    Up 7 minutes                                                      friendly_banzai
54ddd2c51ccd   nginx              "/docker-entrypoint.…"   26 minutes ago   Up 26 minutes               0.0.0.0:80->80/tcp, [::]:80->80/tcp   funny_payne
a5544734a4c6   nginx              "/docker-entrypoint.…"   27 minutes ago   Created                                                           adoring_hopper
67b2efd1e05a   hello-world        "/hello"                 35 minutes ago   Exited (0) 35 minutes ago                                         laughing_blackwell
2cab69e33543   hello-world        "/hello"                 35 minutes ago   Exited (0) 35 minutes ago                                         blissful_torvalds
172a1c098bba   hello-world        "/hello"                 2 days ago       Exited (0) 2 days ago                                             gifted_golick
55b4ef0d918e   devips-utilities   "python main.py"         3 days ago       Exited (0) 3 days ago                                             eager_grothendieck
6c36f313b1e7   ubuntu             "bash"                   3 days ago       Exited (0) 3 days ago                                             great_mestorf
becb538636ed   hello-world        "/hello"                 3 days ago       Exited (0) 3 days ago                                             pensive_panini
2c35583a2db8   hello-world        "/hello"                 3 days ago       Exited (0) 3 days ago                                             unruffled_golick
ce4150f46050   nginx              "/docker-entrypoint.…"   3 days ago       Created                                                           cranky_fermat
0f1c4368aaf5   ubuntu             "/bin/bash"              3 days ago       Exited (137) 3 days ago                                           zen_babbage
4064c0f7c06a   ubuntu             "/bin/bash"              5 days ago       Exited (137) 5 days ago                                           flamboyant_roentgen

Stop and remove a container

ubuntu@ip-172-31-23-28:~$ docker stop 54d
54d
ubuntu@ip-172-31-23-28:~$ docker rm 54d
54d
ubuntu@ip-172-31-23-28:~$ docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
9044a7f8bd7e   ubuntu    "/bin/bash"   8 minutes ago   Up 8 minutes             friendly_banzai


Run a container in detached mode — what's different?

ubuntu@ip-172-31-23-28:~$ docker run -d -p 80:80 nginx
593f587b6e26094f0177eeae31f3ec22331f73b19955887f0385ac8c298d628f

what's different?
it means the contaier run in back ground and return to its terminal immediately even if you close ssh
it keeps running and even if you running it in background you ca still go into it by running command_
dpcker exec =it 593 bash

ubuntu@ip-172-31-23-28:~$ docker run -d -p 80:80 nginx
593f587b6e26094f0177eeae31f3ec22331f73b19955887f0385ac8c298d628f
ubuntu@ip-172-31-23-28:~$ docker exec -it 593 bash

2. Give a container a custom name

ubuntu@ip-172-31-23-28:~$ docker run -d --name myubuntu-server ubuntu
fa28b3d4e7eb728c66b8b80b2483cf859df64b4f0c595b4c1ec53e90f8260687
ubuntu@ip-172-31-23-28:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                 NAMES
593f587b6e26   nginx     "/docker-entrypoint.…"   9 minutes ago   Up 9 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   vigilant_kilby
ubuntu@ip-172-31-23-28:~$ docker ps -a
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
fa28b3d4e7eb   ubuntu             "/bin/bash"              30 seconds ago   Exited (0) 29 seconds ago                                         myubuntu-server
0beeed51e84f   nginx              "/docker-entrypoint.…"   2 minutes ago    Created                                                           nginx-server
593f587b6e26   nginx              "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes               0.0.0.0:80->80/tcp, [::]:80->80/tcp   vigilant_kilby

3. Map a port from the container to your host

   ubuntu@ip-172-31-23-28:~$ docker run -d -p 5000:80 nginx
c19baec65ef09888abfc7e367cb4c70fd4d3d7af42f270f8af24790db90435e7
ubuntu@ip-172-31-23-28:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                     NAMES
c19baec65ef0   nginx     "/docker-entrypoint.…"   4 seconds ago   Up 4 seconds   0.0.0.0:5000->80/tcp, [::]:5000->80/tcp   objective_montalcini

4. Check logs of a running container

   ubuntu@ip-172-31-23-28:~$ docker logs c19
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/02/27 06:01:37 [notice] 1#1: using the "epoll" event method
2026/02/27 06:01:37 [notice] 1#1: nginx/1.29.5
2026/02/27 06:01:37 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19)
2026/02/27 06:01:37 [notice] 1#1: OS: Linux 6.17.0-1007-aws
2026/02/27 06:01:37 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/02/27 06:01:37 [notice] 1#1: start worker processes
2026/02/27 06:01:37 [notice] 1#1: start worker process 29
150.129.44.216 - - [27/Feb/2026:06:04:07 +0000] "GET / HTTP/1.1" 200 615 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36 Edg/145.0.0.0" "-"
2026/02/27 06:04:08 [error] 29#29: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 150.129.44.216, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "54.87.22.197:5000", referrer: "http://54.87.22.197:5000/"
150.129.44.216 - - [27/Feb/2026:06:04:08 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://54.87.22.197:5000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36 Edg/145.0.0.0" "-"
172.17.0.1 - - [27/Feb/2026:06:04:50 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/8.5.0" "-"


5. Run a command inside a running container

   ubuntu@ip-172-31-23-28:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                     NAMES
c19baec65ef0   nginx     "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes   0.0.0.0:5000->80/tcp, [::]:5000->80/tcp   objective_montalcini
ubuntu@ip-172-31-23-28:~$ docker exec -it c19 bash
root@c19baec65ef0:/# ls
bin  boot  dev  docker-entrypoint.d  docker-entrypoint.sh  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@c19baec65ef0:/#


















