# ROS


```
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m -v <AbsolutePathOnHost>:/home/ubuntu/shared --name roboticapoli vossgit/roboticapoli:final
```


mi sono creato una cartella lab e ho sostituito con la sua path assoluta <br>
```<AbsolutePathOnHost> -> /Users/gabrielvoss/Documents/lab```

In questa cartella troverò i catkin_ws che potrò modificare dalla host machine




per entrare nella CLI dalla hostmachine
```
docker exec -it roboticapoli /bin/sh
```

per entrare nella GUI da VNC
http://localhost:6080




per far partire il container le volte successive invece che usare docker run si usa

```
docker start roboticapoli
```



# Spazio catkin preconfigurato

per andarer allo spazio catkin dal terminale docker sulla host machine
```
cd home/ubuntu/shared/catkin_ws
```

dalla GUI ubuntu

basta aprire un terminale e ci si ritrova subito nella cartella catkin_ws

e si trova in 
```
home/ubuntu/shared/catkin_ws
```


questa cartella si trova anche sulla propria macchina hostmachine su

AbsolutePathOnHost/catkin_ws/



# se volgio aggiungere uno spzaio catkin

---
è meglio farlo dalla GUI di ubuntu perchè cosi le cartelle sono modificabili sia dalla host machine che dall'interno della gui vnc


creazione di uno spazio catkin
```
cd /home/ubuntu/condivisa
mkdir -p /catkin_ws2/src
cd /catkin_ws2/

catkin_make
```

per fare il source dello spazio catkin(basterà farlo 1 volta)
```

echo "source /home/ubuntu/condivisa/catkin_ws2/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo printf "source /home/ubuntu/condivisa/catkin_ws2/devel/setup.bash\n" >> /home/ubuntu/.bashrc
source /home/ubuntu/.bashrc

```
