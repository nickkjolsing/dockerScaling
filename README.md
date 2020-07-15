# How to scale docker containers
Tutorial on how to use docker to spin up multiple of the same container



Notes from: https://medium.com/@ainaleke/spinning-up-and-managing-multi-container-apps-using-docker-compose-d0d9f1e4d8ae

# Docker cheatsheet
- ```docker-compose config``` while developing to test if the file has any errors.
- ```services:``` allow you to start things up before the rest of the file runs. 
    - If it is the first time running the services then use ```docker-compose up -d --build```
        - ```-d``` keeps it up and running in the background. Otherwise it would show what the container is doing on the window, but you cant type anymore commands unless you open a new window
    - If you make a change and want to relaunch the container without having to use ```docker-compose down``` then use ```docker-compose up -d --build --force-recreate -t 0```
- Update all images: ```docker-compose pull```
- Update single images: ```docker-compose pull plex```
- ```docker-compose up -d``` updates all the required containers upon running

# Scaling in Docker

- To scale up:
    - ```docker-compose up -d --scale <service name in compose file>=<enter number want scaled to>```
    - Ex: ```docker compose up -d --scale plex=25```
        - Oh also make sure that the ports that the service are mapped to in the ```docker-compsoe``` are different for each container spun up. So make sure 
        - IF you are not trying to spin up completely new containers with this command (maybe you want to use an updated image and spin it up to many without recreating the entire Docker container) use: ```--no-recreate```!

## Example





[example](https://media2.giphy.com/media/lPF7CLMel8QxXDS86U/giphy.gif)