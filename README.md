# List of Useful Docker commands 
## Installation and service
### Daemon start
`sudo systemctl start docker`
## Create Docker Images
### Create docker Image from dockerhub
`sudo docker pull <DockerfileName>`
### Create docker Image from Docker file
`sudo docker build <Dockerfile Location> -t <ImageName>`

## Docker Start up
### Docker Start up without TTY (Background)
`sudo docker run -d <ImageName>`
### Basic start up with TTY attached
`sudo docker run --name <InstanceName> -it <EntryPointCMD>`
### Docker Start up with specific TTY (e.g. stdin/stdout/stderr) attached
`sudo docker run -a stdin -a stdout -i -t <ImageName> <CMD>`
### Docker Exec a command
`sudo docker exec <InstanceName/ID> -it <CMD>`
### Start up with a name
`sudo docker run -it --name <InstanceName/ID> <ImageName> <EntryPointCMD>`
### Start with common PID namespace
`sudo docker run -it --name <InstanceName/ID> --pid=host <ImageName> <EntryPointCMD>`
### Start with common IPC
`sudo docker run -it --name <InstanceName/ID> --ipc=host <ImageName> <EntryPointCMD>`
### Save exited container with changes
Exit from the current docker and check `sudo docker ps --filter "name=<container name>"`
`sudo docker commit <containerID> <ImageName>`
## Docker Export
###
`sudo docker export`


## Docker monitoring
### list of all Instances
`sudo docker ps -a`
### List of process(es) running inside container
`sudo docker top <InstanceName/ID>`

## Docker with X11
### Without python support
* In Host `xauth list| awk 'NR==1'` to get the COOKIE
* In container 
	- `touch /root/.Xauthority`
	- `xauth add <COOKIE>`
	- `xauth list`

### Alternate
`sudo python3 -m pip install dockerx --user`
`sudo python3 -m dockerx.run --image <ImageName> --command 'sleep infinity'`

## Docker termination
### Kill "Exited" Instances
`sudo docker ps -a |grep Exited |awk '{ print $1 }' > /tmp/out.tmp ; xargs --null sudo docker rm < <(tr \\n \\0 </tmp/out.tmp)`
### Terminate and remove an Instance
`sudo docker kill <InstanceName/ID>; sudo docker rm <InstanceName/ID>`
### Terminate and remove all Instances
`sudo docker kill $(sudo docker ps -q); sudo docker rm $(sudo docker ps -a -q)`
## Docker complete uninstallation
```dpkg -l | grep -i docker | awk '{system(" sudo apt purge -y "$2)}';
sudo apt-get remove docker docker-engine docker.io containerd runc;
sudo apt autoremove
```

# List of Useful Docker-compose commands 
## Pull
`sudo docker-compose -f docker-compose.yaml pull`
## Build
`sudo docker-compose -f docker-compose.yaml up -d`
## Kill
`sudo docker-compose -f docker-compose.yaml kill`
## Exec particular service
`docker-compose exec sctp-client bash`
`docker-compose exec sctp-server bash`
