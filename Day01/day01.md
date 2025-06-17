Try to install Docker
```
curl -fsSL https://get.docker.com | sh
```
Docker was already installed, apt update has some errors (broken amnezia repository, multiply debian repository strings)
```
docker --version
```
Fix apt update errors:
```
sudo nano /etc/apt/sources.list
rm /etc/apt/sources.list.d/amnezia-ubuntu-ppa-questing.list
rm /etc/apt/trusted.gpg.d/amnezia_ubuntu_ppa.gpg
```
Download and run nginx docker image:
```
docker run -d -p 8080:80 --name mynginx nginx
docker ps
```
Check nginx work:
```
curl http://localhost:8080
```