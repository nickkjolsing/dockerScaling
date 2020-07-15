# How to scale docker containers
![Image of Docker](https://www.docker.com/sites/default/files/d8/styles/role_icon/public/2019-07/horizontal-logo-monochromatic-white.png?itok=SBlK2TGU)

# Scaling in Docker
##### In this situation I'm using Plex, cause I like Plex. This can be any container you'd like. Such as httpd Apache webservers or MySQL databases

### Step 1: Setup ```docker-compose``` file
# 
```docker-compose``` for some Plex containers!
```
---
    version: "3.8"
    services:
        plex:
            image: linuxserver/plex
            network_mode: host
            environment: 
                - PUID=1000
                - PGID=1000
                - VERSION=docker
            volumes:
                - /home/ubuntu/dockerScale/plex/config
                - /home/ubuntu/dockerScale/plex/movies
```
# 

### Step 2: Execute ```docker-compose``` command

```docker-compose up -d --scale <name of service in compose>=<number of containers>```


Example:
```docker-compose up -d --scale plex=5```
- ```docker-compose up -d``` starts the ```docker-compose.yml``` file in the background
- ```--scale plex=5``` tells it to create 5 containers of the service "plex" from my ```docker-compose.yml```
# 
![example](https://media2.giphy.com/media/lPF7CLMel8QxXDS86U/giphy.gif)
# 

#### Important side-notes
- Make sure that if you name your containers, they each have a unique name
- If you need to map ports within ```docker-compose.yml``` make sure that *each* container is assigend a different port
    - Example: ports section of ```docker-compose.yml``` for an Apache webserver (httpd)
```    
    ports:
        - 80-85:8080 
``` 
- This will assign 80,...,85 in ascending order to the 5 containers created and expose them to 8080
# 

#### Extra features wooo!
- If the container already exists, don't recreate it
    - Add ```--no-recreate``` to ```docker-compose up``` command
# 






Helpful sources: 
- https://medium.com/@ainaleke/spinning-up-and-managing-multi-container-apps-using-docker-compose-d0d9f1e4d8ae
- https://hub.docker.com/r/linuxserver/plex/