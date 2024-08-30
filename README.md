# Gazebo-Installation

Before attempting to install the gazebo_ros_pkgs, make sure the stand-alone Gazebo works by running in terminal:

```bash
   gazebo
```
You should see the GUI open with an empty world. 

## If Gazebo is not installed, you can install it using the following command:

```bash
   curl -sSL http://get.gazebosim.org | sh
```

Run

```bash
   gazebo
```
## Install gazebo_ros_pkgs

Install Pre-Built Debian\Ubuntu binary packages:

```bash
   sudo apt-get install ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control
```
If you do not have a catkin workspace setup, try the following commands:
```bash
   mkdir -p ~/catkin_ws/src
   cd ~/catkin_ws/src
   catkin_init_workspace
   cd ~/catkin_ws
   catkin_make
```
Then add to your .bashrc file a source to the setup scripts:
```bash
   echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

Make sure git is installed on your Ubuntu machine:
```bash
   sudo apt-get install git
```
Noetic is using the gazebo 11.x series, start by installing it:
```bash
   sudo apt-get install -y libgazebo11-dev
```

Download the source code from the gazebo_ros_pkgs github repository:
```bash
   cd ~/catkin_ws/src
   git clone https://github.com/ros-simulation/gazebo_ros_pkgs.git -b noetic-devel

```
Check for any missing dependencies using rosdep:
```bash
   rosdep update
   rosdep check --from-paths . --ignore-src --rosdistro noetic
```
You can automatically install the missing dependencies using rosdep via debian install:
```bash
   rosdep install --from-paths . --ignore-src --rosdistro noetic -y
```
To build the Gazebo ROS integration packages, run the following commands:
```bash
   cd ~/catkin_ws/
   catkin_make
```
## Testing Gazebo with ROS Integration

Source the catkin setup.bash if it's not already in your .bashrc:
```bash
   source ~/catkin_ws/devel/setup.bash
```
Run:
```bash
   roscore &
   rosrun gazebo_ros gazebo
```
