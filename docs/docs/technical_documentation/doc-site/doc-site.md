## Local Documentation Site

In order to refresh the waffles documentation:

Rebuild docker container:
`docker build -t waffles-docs .`

Stop Docker Container:

`docker ps -a | grep 8000 | docker stop $(awk '{print $1}')`

Start Docker Container:

`docker run -d --rm --init --ip 192.168.0.187 -p 8000:8000 waffles-docs:latest`

Bash Script:

```bash
cd /home/noodles/Desktop/omg/waffles
docker build -t waffles-docs .
docker ps -a | grep 8000 | docker stop $(awk '{print $1}')
docker run -d --rm --init --ip 192.168.0.187 -p 8000:8000 waffles-docs:latest
```
