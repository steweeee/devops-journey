Create day2 directory
```
mkdir -p ~/devops-journey/notes/day02 && cd ~/devops-journey/notes/day02
```

Create index.html file
```
nano index.html
```

```
<!-- index.html -->
<!DOCTYPE html>
<html>
<head><title>DevOps Day 2</title></head>
<body><h1>Hello from my Docker container!</h1></body>
</html>
```

Create Dockerfile
```
nano Dockerfile
```

```
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

Build image with name "mynginx" and tag "day2"
```
docker build -t mynginx:day2 .
```

Show images
```
docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
mynginx      day2      f7c0b3ad229f   29 minutes ago   48.2MB
nginx        latest    1e5f3c5b981a   2 months ago     192MB
nginx        alpine    6769dc3a703c   2 months ago     48.2MB
```
Run container with name "mynginx-day2"
```
docker run -d -p 8081:80 --name mynginx-day2 mynginx:day2
```

Check containers
```
docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
d5d6502a233a   mynginx:day2   "/docker-entrypoint.…"   22 minutes ago   Up 22 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   mynginx-day2
```

Check result
```
curl http://localhost:8081
```

Just check nginx:alpine container in interactive mode
```
docker run -it --rm nginx:alpine sh
```