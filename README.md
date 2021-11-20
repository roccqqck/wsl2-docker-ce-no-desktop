# wsl2-docker-ce-no-desktop

## install docker-ce without docker desktop and run
1. install wsl2 ubuntu20.04

2. install docker-ce in wsl2
```
 curl -fsSL https://get.docker.com -o get-docker.sh
 sudo sh get-docker.sh
```

3. copy ```daemon.json``` to ```/etc/docker/```

4. replace ```/lib/systemd/system/docker.service``` with ```docker.service```

5. start docker
```
sudo service docker start
```
if it failed, try

```
sudo nohup dockerd &
```


## let vscode remote container works

5. add win10 env variable ```DOCKER_HOST``` = ```tcp://127.0.0.1:2375```
   
6. download https://download.docker.com/win/static/stable/x86_64/docker-20.10.11.zip 

   extract it to ```C:\\Users\username\programs\docker\```

7. add win10 env variable PATH ```C:\\Users\username\programs\docker\```

   check docker command in Powershell
```
docker ps
```
```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES     SIZE
```
```
docker run -itd -p 8080:80 --name nginx nginx:stable
```
7.  vscode ```setting.json``` add one line ```{"docker.host": "tcp://127.0.0.1:2375"}```
8.  vscode -> Remote Explorer -> Containers -> click ```nginx:stable```

