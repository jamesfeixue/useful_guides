#Building Containerized Applications on AWS

## Introduction

VM e.g. EC2 - mimicking hardware environment, all os, resoources, and internal componenets used by tools or application - wasted resources
containers: share underlying os, binaries, drivers - lightter instantiation, less duplication and waste

Docker
	- Daemon: installed on host machine, brain of docker, creates and manages docker images
		○ find coontainer, access to netowrk ports, storage voluates, etc
	- Client: CLI - command line interface
		○ docker stop
		○ docker create
		○ docker rm
		○ docker start
	- Image Registry
		○ push or pull images as needed (share or deploy)
		○ can be private or public
		○ e.g. Docker Hub or ECR - elastic container registry
		○ container: running instance of a docker image
		○ docker file: text file in a standardized template
			§ dependencies, source code, configurations
		○ docker image - executable, packaged configuration similar to EC2 image


### Commands
- FROM: sets base images e.g. ubuntu:16.04; can also use image as base image
- LABEL: add metadata to image
- RUN: run shell commands `apt-get install -7 python-pip python-dev`
- COPY `./requirements.txt /app/requirements.txt` : copy file from the machine the Docker file is being built on into the image
- WORKDIR /app : working diretory for any subsequent instruction that will be run, if the directory doesn't exist, this will create it
RUN pip install -r requirements.text
COPY . /app
	- copy all the source code into working directory
EXPOSE 8080 
	- port for the container to communicate on if yoou want container to be able to communcate with external entities like other container or remote services
ENTRYPOINT ["python"]
	- what script or command you want to run when the container starts up
	- static once it's been defined
	- can be overriden with --entrypoint flag
CMD ["app.py"]
	- execute commands or scripts at runtime, allows you to provide default values and can pass in values via the command line to override default values at runtime

docker inspect
layers
	- each layer is a diff, read only
	- common layers between images can be shared; minimized 
	- union file system
	- writable layers and read only layers
	- copy-on-write strategy
	- persistent data: Docker volumes, outside life cycle of container, share data across containers

Docker CLI and Logging



