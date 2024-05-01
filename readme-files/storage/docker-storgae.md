# Docker storage
[By default docker stores the files under the "/var/lib/docker/" directory path]
[Containing the below directories and files]

[
drwx--x--x   buildkit
drwx--x---   containers
-rw-------   engine-id
drwx------   image
drwxr-x---   network
drwx--x---   overlay2
drwx------   plugins
drwx------   runtimes
drwx------   swarm
drwx------   tmp
drwx-----x   volumes
]

# Docker Images
[When biulding the "Docker images" its using the layered architecture]
[Explain this using the below Dockerfile]
[
    FROM:   ubuntu:latest
    RUN:    apt-get update && apt upgrade -y
    RUN:    apt-get install nginx -y
    CMD:    ["nginx"]
]
[When creating the Docker image, it will use the "Base ubuntu layer"] <<-- 1st layer
[Then updates will be the second layer] <<-- 2nd layer
[Installing the Nginx package will the the third layer] <<-- 3rd layer
[Final layer will the cmd layer] <<-- 4th layer

[Then create another image using the below Dockerfile]
[
    FROM:   ubuntu:latest
    RUN:    apt-get update && apt upgrade -y
    RUN:    apt-get install nginx -y
    RUN:    apt-get install mysql -y
    CMD:    ["nginx"]
]

[When its building the image inside the same machine, it will not going to perform the all previous steps]
[It will reuse the previously created layers]
[
    FROM:   ubuntu:latest   <<-- From 1st layer
    RUN:    apt-get update && apt upgrade -y    <<-- From 2nd layer
    RUN:    apt-get install nginx -y    <<-- From 3rd layer
    RUN:    apt-get install mysql -y    <<-- New layer
    CMD:    ["nginx"]
]

[After building the images, cannot modify it] <<-- Image layer || Its read only
[After creating a container using the created image, can modify the files of it]
[Because, container having the copy of files] <<-- Container layer || Read Write

# Volumes
[Volumes are using to persist the data of the containers]
[Docker volumes can find in below directory path]
[/var/lib/docker/volumes]
