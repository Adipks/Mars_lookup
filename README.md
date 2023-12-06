# Jetson Nano communication(Wi-Fi)
connect both the Master System and the Slave system to the same Wi-Fi Network
## 1 Know the IP adresses of both your devices
run the script below to know your IP Profile
```
ifconfig
```
check the second line for the inet addr: <192.168.0.104//this is a sample ip adresss> . It is the ip address of your main pc
similarly find the ip adress of the Slave system
## 2 Configuring the .bashrc file
So here is the main thing that needs to be done. We need to say our computer who is the master computer running ROS and what is there’s IP in the network. Since Computers running ROS don’t know there IP address.<br>
First in Master PC open terminal and type:
```
gedit .bashrc
```
go to the bottom of your .bashrc file and paste then save it.
```
export ROS_MASTER_URI=http://localhost:11311/
export ROS_HOSTNAME=192.168.0.104
export ROS_IP=192.168.0.104
```
In first line we specify the address of the master along with the port to operate.<br>
check what ROS_MASTER_URI when you run roscore on master system<br>
replace the ip with your master system's ip adress<br>
we basically say our master PC that you are the Host so in order to specify the IP address we say take your own localhost IP address.<br>
finally source your .bashrc file
```
source .bashrc
```
Follow the same steps on the Slave system<br>
for more info visit
https://razbotics.wordpress.com/2018/01/23/ros-distributed-systems/
## Alternate methods
```
ssh marsjetson@marsjetson-desktop.local
```
directly ssh into the jetson module<br>
### kill command
```
kill -9 [pid of roscore]
```
