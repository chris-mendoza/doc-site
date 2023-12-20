## Docker

This documentation runs on docker.

The Dockerfile contains an `ENTRYPOINT` and `CMD` that runs `mkdocs serve -a0.0.0.0:8000`.

### Refresh Documentation:

#### Copy Files:

As root:

`rsync -avz /home/noodles/Desktop/omg/waffles/ /home/waffles/docs/`

Switch user to waffles:

`su - waffles`

Run build command:

`docker build -t waffles-docs docs`

Run build command as root as waffles:
`sudo -u waffles docker build -t waffles-docs /home/waffles/docs`

#### Stop Doc Server

`sudo -u waffles docker ps -a | grep 8000 | docker stop $(awk '{print $1}')`

#### Start Doc Server

`sudo -u waffles docker run -d --rm --init --ip 192.168.0.187 -p 8000:8000 waffles-docs:latest`

#### Running Docker Container Status

`docker ps`

#### Start Docker Server

`docker run -it --rm --init --ip 192.168.0.187 -p 8000:8000 waffles-docs:latest`

#### Stop Docker Container

`docker stop <container id>`
