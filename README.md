# my-UBmate-ROS-env-setup
Description of my robotic computing platform eviroment setup based on Rpi with ubuntu mate 16.x running ROS Kinetic

1. HW Ingredients
- Rpi 3 B 
- 5V power suppy
- micro SD card >8GB
- keyboard/mouse/HDMI monitor
- internet connection
- another computer/laptop with Win10 + Win32DiskImager + an ssh client

2. Download Ubuntu Mate for Rpi
  https://ubuntu-mate.org/download/
  use the image file:
  https://ubuntu-mate.org/raspberry-pi/ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img.xz
  
3. Use Win32 disk imager to clone the image file to an SD card and leave your computer taking a cup of coffee!

4. When its done, remove the SD card from your computer and place it to your Rpi and let it boot up.

5. Setup basic stuff needed for Ubuntu mate and get a ssh server:
  sudo apt-get update
  sudo apt-get install openssh-server
  sudo ufw allow 22
  sudo /etc/init.d/ssh restart
  
 6. What you find below are the steps to install ROS Kinetic on the Raspberry Pi 3.
 Source:https://www.intorobotics.com/how-to-install-ros-kinetic-on-raspberry-pi-3-ubuntu-mate/
 
Step 1: Go to System -> Administration -> Software & Updates

Step 2: Check the checkboxes to repositories to allow “restricted,” “universe,” and “multiverse.

Step 3: Setup your sources.list
  
>sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Step 4: Setup your keys
  
>wget http://packages.ros.org/ros.key -O - | sudo apt-key add -

Step 5: To be sure that your Ubuntu Mate package index is up to date, type the following command
  
>sudo apt-get update

Step 6: Install ros-kinetic-desktop-full
 
>sudo apt-get install ros-kinetic-desktop-full

Step 7: Initialize rosdep

>sudo rosdep init
>rosdep update

Step 8: Setting up the ROS environment variables
>echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
>source ~/.bashrc

Step 9: Create and initialize the catkin workspace
>mkdir -p ~/catkin_workspace/src
>cd catkin_workspace/src
>catkin_init_workspace
>cd ~/catkin_workspace/
>catkin_make

Step 10: Add the catkin_workspace to your ROS environment
>source ~/catkin_workspace/devel/setup.bash
>echo “source ~/catkin_workspace/devel/setup.bash” >> ~/.bashrc

Step 11: Check the ROS environment variables
>export | grep ROS
