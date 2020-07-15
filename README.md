# How to scale docker containers
Tutorial on how to use docker to spin up multiple of the same container

# Scaling in Docker

- To scale up:
    - ```docker-compose up -d --scale <service name in compose file>=<enter number want scaled to>```
    - Ex: ```docker compose up -d --scale plex=25```
        - Oh also make sure that the ports that the service are mapped to in the ```docker-compsoe``` are different for each container spun up. So make sure 
        - IF you are not trying to spin up completely new containers with this command (maybe you want to use an updated image and spin it up to many without recreating the entire Docker container) use: ```--no-recreate```!

## Example





![example](https://media2.giphy.com/media/lPF7CLMel8QxXDS86U/giphy.gif)

Sources: 
- https://medium.com/@ainaleke/spinning-up-and-managing-multi-container-apps-using-docker-compose-d0d9f1e4d8ae
- https://hub.docker.com/r/linuxserver/plex/