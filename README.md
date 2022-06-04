## Create Docker Images
### Create docker Image from Docker file
`sudo docker build <Dockerfile Location> -t <ImageName>`

## Docker Start up
### Basic start up with TTY attached
`sudo docker run --name <InstanceName> -it <EntryPointCMD>`
### Docker Start up with specific TTY (e.g. stdin/stdout/stderr) attached
`sudo docker run -a stdin -a stdout -i -t <ImageName> <CMD>`
### Docker Start up without TTY
`sudo docker run -d -p 80:80 my_image service <ImageName>`
### Docker Exec a command
`sudo docker exec <InstanceName/ID> -it <CMD>`
### Start up with a name
`sudo docker run -it --name <InstanceName> <ImageName> <EntryPointCMD>`

### Start with common pid space
`sudo docker run -it --pid=host <ImageName> <EntryPointCMD>`
### Start with common IPC
`sudo docker run -it --ipc=host <ImageName> <EntryPointCMD>`

## Docker monitoring
### list of all Instances
`sudo docker ps -a`

## Docker termination
### Terminate and remove an Instance
`sudo docker kill <InstanceName/ID>; sudo docker rm <InstanceName/ID>`
### Terminate and remove all Instances
`sudo docker kill $(sudo docker ps -q); sudo docker rm $(sudo docker ps -a -q)`
