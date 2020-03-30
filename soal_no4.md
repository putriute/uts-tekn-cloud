penjelasan soal_no4

$ docker ps

$ docker -v
perintah docker -v digunakan untuk cek versi docker

$ docker images
digunakan untuk memeriksa apakah sudah terdapat docker images 

$ docker search nginx
Terdapat beberapa docker images yang bisa kita gunakan yaitu dengan mengambil images dari lokasi docker hub (memerlukan koneksi internet). perintah ini digunakan untuk mencari docker imagesnya

$ docker pull nginx
digunakan untuk mengambil images tersebut

$ docker rmi nama_image -f
digunakan untuk menghapus image

$ docker ps -l
perintah ini digunakan untuk cek docker container list

$ docker run -d -p 8080:80 --name nginx-1 nginx
perintah ini digunakan untuk membuat docker container
> –name nginx-1 berfungsi untuk memberi nama container dengan nama nginx-1 (biasanya digunakan untuk memudahkan delete container dan lainnya)
-p 8080:80 untuk port forwarding dari 8080 port tujuan ke port 80 asal aplikasi (forward port 80 ke port 8080)
-d tanpa isian parameter, digunakan untuk menjalankan perintah sebagai daemon (background service, tanpa log di terminal)

$ netstat -lnpt
perintah ini digunakan untuk mengecek network status

$ docker run -d -p 8082:80 --name nginx-2 nginx
$ docker run -d -p 8083:80 --name nginx-3 nginx
pada perintah diatas bisa run beberapa container sekaligus dari images yang sama. caranya dengan jalankan docker run dengan port yang berbeda-beda

$ docker extc -it nginx-1 /bin/bash
perintah ini digunakan untuk masuk ke dalam docker container




program
URL :https://beril.id/pengertian-dari-docker-serta-cara-penggunaannya/

[node1] (local) root@192.168.0.23 ~
$ docker pull mongo:latest
latest: Pulling from library/mongo
Digest: sha256:1e33093260855e83baee0237e29947e243818c58a1d37b1022909e227f624d7a
Status: Image is up to date for mongo:latest
docker.io/library/mongo:latest

[node1] (local) root@192.168.0.23 ~
$ docker run -v "$(pwd)":/dta --name mongo -d mongo mongod --smallfiles
547ca4df4b6b731d16c9dadf3a55f57ff8613b9685e248ee2c1ebf9f3cc88f47

[node1] (local) root@192.168.0.23 ~
$ docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS               NAMES
0a0489f8f0b1        mongo:latest           "docker-entrypoint.s…"   6 minutes ago       Up 5 minutes        27017/tcp           pwd_mongo.1.c7uf5kujgmlrhukkv1km2g7c0
f53974724eb9        mongo-express:latest   "tini -- /docker-ent…"   6 minutes ago       Up 5 minutes        8081/tcp            pwd_mongo-express.1.dxqiviz7erd6az7t0euc23pmb

[node1] (local) root@192.168.0.23 ~
$ docker -v
Docker version 19.03.4, build 9013bf583a

[node1] (local) root@192.168.0.23 ~
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mongo               latest              c5e5843d9f5f        2 days ago          387MB
mongo-express       latest              a36d72e09c39        4 days ago          127MB

[node1] (local) root@192.168.0.23 ~
$ docker search nginx
NAME                               DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
nginx                              Official build of Nginx.                        12893               [OK]                
jwilder/nginx-proxy                Automated Nginx reverse proxy for docker con…   1758                                    [OK]
richarvey/nginx-php-fpm            Container running Nginx + PHP-FPM capable of…   760                                     [OK]
linuxserver/nginx                  An Nginx container, brought to you by LinuxS…   101                                     
bitnami/nginx                      Bitnami nginx Docker Image                      80                                      [OK]
tiangolo/nginx-rtmp                Docker image with Nginx using the nginx-rtmp…   66                                      [OK]
jc21/nginx-proxy-manager           Docker container for managing Nginx proxy ho…   46                                      
nginxdemos/hello                   NGINX webserver that serves a simple page co…   44                                      [OK]
jlesage/nginx-proxy-manager        Docker container for Nginx Proxy Manager        36                                      [OK]
nginx/unit                         NGINX Unit is a dynamic web and application …   36                                      
nginx/nginx-ingress                NGINX Ingress Controller for Kubernetes         28                                      
privatebin/nginx-fpm-alpine        PrivateBin running on an Nginx, php-fpm & Al…   23                                      [OK]
schmunk42/nginx-redirect           A very simple container to redirect HTTP tra…   18                                      [OK]
blacklabelops/nginx                Dockerized Nginx Reverse Proxy Server.          13                                      [OK]
centos/nginx-18-centos7            Platform for running nginx 1.8 or building n…   13                                      
nginxinc/nginx-unprivileged        Unprivileged NGINX Dockerfiles                  13                                      
raulr/nginx-wordpress              Nginx front-end for the official wordpress:f…   12                                      [OK]
centos/nginx-112-centos7           Platform for running nginx 1.12 or building …   12                                      
nginx/nginx-prometheus-exporter    NGINX Prometheus Exporter                       10                                      
sophos/nginx-vts-exporter          Simple server that scrapes Nginx vts stats a…   7                                       [OK]
mailu/nginx                        Mailu nginx frontend                            6                                       [OK]
bitnami/nginx-ingress-controller   Bitnami Docker Image for NGINX Ingress Contr…   4                                       [OK]
ansibleplaybookbundle/nginx-apb    An APB to deploy NGINX                          1                                       [OK]
wodby/nginx                        Generic nginx                                   0                                       [OK]
centos/nginx-110-centos7           Platform for running nginx 1.10 or building …   0                                       
[node1] (local) root@192.168.0.23 ~
$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
68ced04f60ab: Pull complete 
28252775b295: Pull complete 
a616aa3b0bf2: Pull complete 
Digest: sha256:2539d4344dd18e1df02be842ffc435f8e1f699cfc55516e2cf2cb16b7a9aea0b
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

[node1] (local) root@192.168.0.23 ~
$ docker rmi nama_image -f
Error: No such image: nama_image

[node1] (local) root@192.168.0.23 ~
$ docker ps -l
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
547ca4df4b6b        mongo               "docker-entrypoint.s…"   33 minutes ago      Exited (2) 33 minutes ago                       mongo

[node1] (local) root@192.168.0.23 ~
$ docker run -d -p 8080:80 --name nginx-1 nginx
7e84ca9b4cda80508cbe47f41ea0012b8426276cdd24d3b5ede173b71311565e

[node1] (local) root@192.168.0.23 ~
$ netstat -lnpt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.11:42280        0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      32/sshd
tcp        0      0 :::2375                 :::*                    LISTEN      16/dockerd
tcp        0      0 :::2377                 :::*                    LISTEN      16/dockerd
tcp        0      0 :::7946                 :::*                    LISTEN      16/dockerd
tcp        0      0 :::8080                 :::*                    LISTEN      56604/docker-proxy
tcp        0      0 :::8081                 :::*                    LISTEN      16/dockerd
tcp        0      0 :::22                   :::*                    LISTEN      32/sshd

[node1] (local) root@192.168.0.23 ~
$ http://localhost:8080
bash: http://localhost:8080: No such file or directory

[node1] (local) root@192.168.0.23 ~
$ docker run -d -p 8082:80 --name nginx-2 nginx
9d02103165d29a4e6ac58c05ee978344996acd94931216ba66929332d95899f4

[node1] (local) root@192.168.0.23 ~
$ docker run -d -p 8083:80 --name nginx-3 nginx
90957925955c6d7d0de0ea9d341f49aa332716047dba35d6ccbee98b959a1815

[node1] (local) root@192.168.0.23 ~
$ http://localhost:8082
bash: http://localhost:8082: No such file or directory

[node1] (local) root@192.168.0.23 ~
$ http://localhost:8083
bash: http://localhost:8083: No such file or directory

[node1] (local) root@192.168.0.23 ~
$ docker extc -it nginx-1 /bin/bash
unknown shorthand flag: 'i' in -it
See 'docker --help'.

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default
                           "/root/.docker")
  -c, --context string     Name of the context to use to connect to the
                           daemon (overrides DOCKER_HOST env var and default
                           context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level
                           ("debug"|"info"|"warn"|"error"|"fatal") (default
                           "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default
                           "/root/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default
                           "/root/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/root/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  app*        Docker Application (Docker Inc., v0.8.0)
  builder     Manage builds
  checkpoint  Manage checkpoints
  config      Manage Docker configs
  container   Manage containers
  context     Manage contexts
  engine      Manage the docker engine
  image       Manage images
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  deploy      Deploy a new stack or update an existing stack
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
