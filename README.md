# All The Mods docker
My docker-compose setup for All The Mods 8

All The Mods 8:  
https://github.com/AllTheMods/ATM-8

itzg docker Minecraft server:  
https://github.com/itzg/docker-minecraft-server

Here is an example for the Docker compose:

```
version: "3"

services:
  minecraft:
    image: ${IMAGE:-itzg/minecraft-server}
    environment:
      EULA: "TRUE"
      TYPE: FORGE
      FORGE_INSTALLER: "forge-1.18.2-40.1.20-installer.jar"
      DIFFICULTY: hard
      VERSION: "1.18.2"
      OVERRIDE_SERVER_PROPERTIES: "TRUE"
      JVM_XX_OPTS:     -Xms6G -Xmx10G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1
      MAX_MEMORY: 16G
      MAX_PLAYERS: 69
      MOTD: "Minecraft ATM 8"
      DIFFICULTY: hard
      SPAWN_PROTECTION: 0
      ENFORCE_WHITELIST: "true"
      WHITELIST: player,name
      OPS: player,name
    ports:
      - 25565:25565
    volumes:
      - PATH-TO-LOCAL-DIRECTORY:/data
    ulimits:
      nofile:
        soft: "65536"
        hard: "65536"
    restart: unless-stopped
```
**NOTE**  
- Set the volume to the correct directory
- Download the Server Files from curseforge and move all the files inside to your server directory
- Use the correct `.jar` file at `FORGE_INSTALLER`
- set the whitelist an op to your preferences

After that, start the docker container
