# First-task
Ubuntu install of ROS Noetic

## 1- Installation Oracle VM VirtualBox Manager
First, I downloaded Oracle VM VirtualBox Manager from this 
[VM link](https://www.virtualbox.org/wiki/Downloads)
To install Linux on a Windows machine
<img width="500" alt="VM" src="https://github.com/Worod44/First-task/assets/95488818/f4620bd8-da94-419a-adaf-f2fa46042956">
<img width="500" alt="VM2" src="https://github.com/Worod44/First-task/assets/95488818/e6043c31-6565-452d-9d08-2e1032fc92d0">
## 2-download Ubuntu 20.04 desktop image
Download Ubuntu 20.04 using VM from the following 
[Ubuntu 20.04 link](https://releases.ubuntu.com/20.04.6/?_ga=2.106549827.1335148733.1689627889-2079856977.1684269564)

And then install it on the Linux system.[Tutorial download Ubuntu link](https://youtu.be/MR1FkDmrQuM):

After downloading Ubuntu, we will open the terminal and write the commands to download **ROS Noetic**


## 3-ROS Noetic installation 
After installing and configuring Ubuntu, I will download the Rose Noetic on it
[ROS Noetic link](http://wiki.ros.org/noetic/Installation/Ubuntu)

#### 3.1 Setup your sources.list
Setup your computer to accept software from packages.ros.org.

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

#### 3.2 Set up your keys

```
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
#### 3.3 Installation
First, make sure your Debian package index is up-to-date:

```
sudo apt update
```
Now pick how much of ROS you would like to install.

##### Desktop-Full Install: (Recommended) :
Everything in **Desktop** plus 2D/3D simulators and 2D/3D perception packages
```
sudo apt install ros-noetic-desktop-full
```
#### 3.4 Environment setup
You must source this script in every bash terminal you use ROS in.
```
source /opt/ros/noetic/setup.bash
```
#### 3.5 Dependencies for building packages
Up to now you have installed what you need to run the core ROS packages. To create and manage your own ROS workspaces, there are various tools and requirements that are distributed separately. For example, rosinstall is a frequently used command-line tool that enables you to easily download many source trees for ROS packages with one command.

**To install this tool and other dependencies for building ROS packages, run:**
```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
##### 3.5.1 Initialize rosdep
Before you can use many ROS tools, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep, do so as follows.
```
sudo apt install python3-rosdep
```

With the following, you can initialize rosdep.
```
sudo rosdep init
rosdep update
```
### 4-Create a workspace
**We install the catkin to create a workspace**
```
sudo apt-get install ros-noetic-catkin
mkdir -p ~/catkin_ws/src

```
**After that, we will install the arms package in the workspace that we created**
```
cd ~/catkin_ws/
catkin_make
cd ~/catkin_ws/src
git clone https://github.com/smart-methods/arduino_robot_arm.git 
cd ~/catkin_ws
```
#### for noetic distro
```
rosdep install --from-paths src --ignore-src -r -y
sudo apt-get install ros-noetic-moveit
sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```
After installing all the commands, we open the bacharc file and add the source to it, using the following commands:
```
sudo nano ~/.bashrc
```
at the end of the (bashrc) file add the follwing line
(source /home/worod/catkin_ws/devel/setup.bash)
then 
ctrl + o

After that, we update the source for bashrc file
```
source ~/.bashrc
```
The last thing to do is to run the Rviz program using the following command
```
roslaunch robot_arm_pkg check_motors.launch
```
<img width="356" alt="p1" src="https://github.com/Worod44/First-task/assets/95488818/207124b6-fe81-4286-8e1f-0863608678f7">
<img width="366" alt="p2" src="https://github.com/Worod44/First-task/assets/95488818/2ae7f85f-8bf5-4df7-8ab4-c57b12206934">






