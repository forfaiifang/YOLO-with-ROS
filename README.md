*Darknet_ros packages have been tested under ROS Kinetic and Ubuntu 16.04*

## **Installation**

1. **Install ROS and make workspace**

Follow the ROS [installation guide](http://wiki.ros.org/ROS/Installation) for download and installation and ROS [tutorials](http://wiki.ros.org/ROS/Tutorials) for creating a workspace.

After creating a workspace, open terminal and run

    cd [workspace]/src
    git clone --recursive git@github.com:leggedrobotics/darknet_ros.git
    cd ../
    catkin_make -DCMAKE_BUILD_TYPE=Release


2. **Provide your weights and your cfg file** inside the directories:    

`[workspace]/src/darknet_ros/darknet_ros/yolo_network_config/weights/`
`[workspace]/src/darknet_ros/darknet_ros/yolo_network_config/cfg/`

3. **Create your config file for ROS** and include it inside:` [workspace]/src/darknet_ros/darknet_ros/config/`
 - Change `name` in line 4 to your cfg name and name in line 6 to your weights file (that you provide above)

 - Edit names of detection classes 1 class per line.

![image](https://user-images.githubusercontent.com/59696434/81466427-dc79a580-91fb-11ea-9b1d-707da76864dd.png)

4. **Edit darknet_ros.launch**  in  `[workspace]/src/darknet_ros/darknet_ros/launch `


You have to point to your new config file in line 13:

    <rosparam command="load" ns="darknet_ros" file="$(find darknet_ros)/config/your_config_file.yaml"/>
    
![image](https://user-images.githubusercontent.com/59696434/81466575-fff12000-91fc-11ea-8630-763fbc773261.png)


5. **Nodes**
You can change the names and other parameters of the publishers, subscribers and actions inside `darknet_ros/config/ros.yaml`

**Example**
Change topic: `/hsrb/head_rgbd_sensor/rgb/image_raw` to subscribe image camera of HSR robot
![image](https://user-images.githubusercontent.com/59696434/81466631-58282200-91fd-11ea-9ef3-fd488e8a4a3e.png)

 6. **Run catkin_make in your workspace**

In terminal

    cd [workspace]/
    catkin_make



## **Test YOLO with ROS**


Example for HSR robot

In a terminal

    hsrb_mode
    cd [workspace]
    source devel/setup.bash

![image](https://user-images.githubusercontent.com/59696434/81466912-53fd0400-91ff-11ea-9d74-551cab80c445.png)

and run

    roslaunch darknet_ros darknet_ros.launch

![image](https://user-images.githubusercontent.com/59696434/81466937-83ac0c00-91ff-11ea-831c-30bb42581375.png)
    
    
**Result**

![image](https://user-images.githubusercontent.com/59696434/81466953-9cb4bd00-91ff-11ea-9382-e0b48c1b834c.png)
