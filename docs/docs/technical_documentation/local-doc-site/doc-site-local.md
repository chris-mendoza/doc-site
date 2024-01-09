Refresh Docs:

```bash
docker build -t waffles-docs .
docker ps -a | grep 8005 | docker stop $(awk '{print $1}')
docker run -d --rm --init --ip 192.168.0.187 -p 8005:8005 waffles-docs:latest
```
