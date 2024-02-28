# ROS


```
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m -v /users/gabrielvoss/documents/GitHub:/github --name roboticapoli vossgit/roboticapoli:latest 

```

```

echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
echo "source /opt/ros/noetic/setup.bash\n" >> /home/ubuntu/.bashrc
source ~/home/ubuntu/.bashrc


cd /home/ubuntu/
mkdir -p /catkin_ws/src
cd /catkin_ws/

catkin_make


echo "source /home/ubuntu/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo printf "source /home/ubuntu/catkin_ws/devel/setup.bash\n" >> /home/ubuntu/.bashrc
source /home/ubuntu/.bashrc

```
