# ROS


```
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m -v /users/gabrielvoss/documents/GitHub:/home/ubuntu/condivisa --name roboticapoli vossgit/roboticapoli:latest 

```

per far partire il container
```
docker start roverchallenge
```

per entrare nella CLI
```
docker exec -it roverchallenge /bin/sh
```

per fare il source di ros(basterà farlo 1 volta)
```

echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
```
echo "source /opt/ros/noetic/setup.bash\n" >> /home/ubuntu/.bashrc
source ~/home/ubuntu/.bashrc


```

creazione di uno spazio catkin
```
cd /home/ubuntu/condivisa
mkdir -p /catkin_ws/src
cd /catkin_ws/

catkin_make
```

per fare il source dello spazio catkin(basterà farlo 1 volta)
```

echo "source /home/ubuntu/condivisa/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo printf "source /home/ubuntu/condivisa/catkin_ws/devel/setup.bash\n" >> /home/ubuntu/.bashrc
source /home/ubuntu/.bashrc

```
