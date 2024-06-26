# ROS NOETIC DOCKER SETUP
![diagram-export-29-2-2024-16_01_37](https://github.com/voss01/ROS/assets/49610092/b9cf01a2-96a0-4710-b81c-5e1a8b7ea4bb)


## update
the image has been updated, if you have already followed this process and dont want to pull the docker image again you can just install this from the terminal inside ubuntu
```
 apt-get install -y net-tools iproute2 ros-noetic-plotjuggler* ros-noetic-foxglove-bridge ros-noetic-turtlesim
```
### Description
This Docker container is set up for running a robotic simulation environment with the following specifications:

**ROS Version:** The container is configured to run with ROS (Robot Operating System) in the "noetic" release.

**Catkin_ws:** This docker setup will provide a preconfigured catkin workspace accessible both on the HOST MACHINE and the UBUNTU os



### Install Docker
[﻿https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/) 

**Possible errors**

- you have to enable hardware assisted virtualization on windows [﻿forums.docker.com/t/hardware-assisted-virtualization-and-data-execution-protection-must-be-enabled-in-the-bios/109073](https://forums.docker.com/t/hardware-assisted-virtualization-and-data-execution-protection-must-be-enabled-in-the-bios/109073) 
- if you have an older version of operating system you may want to install an older version of docker [﻿docs.docker.com/desktop/release-notes/](https://docs.docker.com/desktop/release-notes/) 

# Download the image and run it
This line will download, from docker hub, the docker image if it's not already on your host machine

The image will be then automatically start



- **important note**:
  1. for Mac and linux users in docker before executing the following commands you have to set in preferences -> resources -> file sharing the path to the github folder
  2. for Mac users with M chips (arm) go to docker settings -> general -> enable "Use Rosetta for x86/amd64 emulation on Apple Silicon"


You will have to write to the mount your own folder

**Example** with a Lab folder

```
<AbsolutePathOnHost>
```
the whole string including <> Becomes:

- for MacOS: `/Users/Documents/Lab`
- for Windows: `C:\Users\user\Lab`
- for Linux: `/home/user/Lab`

Having specified `<AbsolutePathOnHost>` in the correct place of the following command you can now execute it (remember to have the docker app open in the backround otherwise it won't work).
<br>
<br>
Docker run will download the image automatically from docker hub and run it.
<br>
<br>
Do not remove or change `:/home/ubuntu/shared` as it is the path of the folder that will be created inside the docker container and where the catkin_ws will be stored.
<br>
<br>
```
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m -v <AbsolutePathOnHost>:/home/ubuntu/shared --name roboticapoli vossgit/roboticapoli:prod
```
At this point you should get as output a bunch of `RUNNING state` lines from vnc and novnc, you can proceed.



### Accessing the cli from docker on HOST MACHINE
```
docker exec -it roboticapoli /bin/sh
```
Inside the shell that will automatically start to use the more useful bash just write next to the # <br>
`bash`


### Accessing the GUI
After running the container, you can access the graphical user interface (GUI) by opening a web browser and navigating to  [﻿http://localhost:6080](http://localhost:6080/). The container exposes the GUI on port 6080, allowing you to interact with the simulation environment.

To restart the container when closed(you should always have the docker app running in the background) in the computer terminal/shell write:docker start roverchallenge



### To restart the container when closed
(you should always have the docker app running in the background) in the computer terminal/shell write:

```
docker start roboticapoli
```
```
docker exec -it roboticapoli /bin/sh
```
`bash`

---

# How to open the preconfigured catkin workspace


There are 2 ways

- from the HOST MACHINE using a shell to access the docker container
- using the UBUNTU GUI using vnc

**first method**
To move to the "catkin_ws" directory from the Docker terminal on the host machine, you can follow these steps:

1. Open a shell with docker`docker exec -it roboticapoli /bin/sh ` then write `bash`
2. Use the command `cd /home/ubuntu/shared/catkin_ws`  to change directory to the "catkin_ws" directory.
3. Now, you're in the "catkin_ws" directory within your Docker container.



**second method**
If you want to access the same directory on UBUNTU:

1. go to  [﻿http://localhost:6080](http://localhost:6080/) 
2. open a terminal with the terminator app and you will be prompted already in the catkin_ws folder (which is inside /home/ubuntu/shared)


Additionally you can find your files and edit them on the HOST MACHINE using your preferred IDE

1. You mentioned the directory exists on your host machine at `AbsolutePathOnHost/catkin_ws/` .






# HOW TO ADD YOUR OWN CATKIN_WS
Because of how the setup is done it's better to follow these steps inside the UBUNTU GUI at [﻿http://localhost:6080](http://localhost:6080/) to make the catkin_ws accessible to everyone.



This is because if you access with the docker shell from the HOST MACHINE you are seen as root user therefore you create folders accessible just to that user, and consequently not modifiable by the shell in UBUNTU GUI



So from [﻿http://localhost:6080](http://localhost:6080/)  open a terrminal (with terminator) and write

```
cd /home/ubuntu/shared
mkdir -p catkin_ws2/src
cd /catkin_ws2/

catkin_make
```
source the work space (this can be done just once)

```
echo "source /home/ubuntu/shared/catkin_ws2/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo printf "source /home/ubuntu/shared/catkin_ws2/devel/setup.bash\n" >> /home/ubuntu/.bashrc
source /home/ubuntu/.bashrc
```


