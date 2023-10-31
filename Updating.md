# Updating the Minecraft Server

Updating currently involves some manual labour but for the sake of creating Backups this is not the worst thing in the world ;)

## Updating
- First, download the new server files from CurseForge and upzip the folder
- Shut down the docker container
- If you want to be extra safe, make a backup of the old server files
- Copy the new server files to the server folder, overwriting the existing files
- update the installer filename in the docker-compose file.
- Start the server again, ideally pulling the newest docker image in the process

