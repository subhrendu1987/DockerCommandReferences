## Create Docker Images
### Create docker Image from Docker file
`sudo docker build <Dockerfile Location> -t <ImageName>`
### Docker Start up
`sudo docker run --name <InstanceName> -it <EntryPointCMD>`
### Docker Start up with specific TTY (e.g. stdin/stdout/stderr) attached
`sudo docker run -a stdin -a stdout -i -t <ImageName> <CMD>`
### Docker Start up without TTY
`sudo docker run -d -p 80:80 my_image service <ImageName>`
### Docker Exec a command
`sudo docker exec <InstanceName/ID> -it <CMD>`
### Start up with a name
`sudo docker run -it --name <InstanceName> <ImageName> <EntryPointCMD>`

###
`sudo docker run -it --pid=host <IamgeName> /bin/bash`
