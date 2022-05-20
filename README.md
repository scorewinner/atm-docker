# atm7-docker
My docker-compose setup for all the mods 7

All The Mods 7:  
https://github.com/AllTheMods/ATM-7

itzg docker Minecraft server:  
https://github.com/itzg/docker-minecraft-server


Since curseforge killed the `simple-server` files, you need to use the `FORGE` tag in the `docker-compose` file. Mine looks as follows:

```
version: "3"

services:
  mc:
    image: ${IMAGE:-itzg/minecraft-server}
    environment:
      EULA: "TRUE"
      TYPE: FORGE
      FORGE_INSTALLER: "forge-1.18.2-40.1.20-installer.jar"
      DIFFICULTY: hard
      ENFORCE_WHITELIST: "true"
    ports:
      - 25565:25565
    volumes:
      - ./atm7:/data
    ulimits:
      nofile:
        soft: "65536"
        hard: "65536"
    restart: unless-stopped
```
**NOTE**  
Use the correct `.jar` file at `FORGE_INSTALLER`


My direcotry is set up as follows:
```
atm7/
docker-compose.yml
```
Place the downloaded server files into the `atm7` directory and edit the files as you need them (server.properties etc.)

After that, start the docker container



**To migrate your old world:**  
Start the server once and shut it down again.  
Replace the `world` folder with your backed up one.
