## Neotic-AVP-Demo
This is a simplified  version of  [This repository](https://github.com/liuguitao/AVP-SLAM-PLUS)， some modifications are made to preserve the basic mapping and localization functions that can be applied to [ROS Neotic](http://wiki.ros.org/noetic/Installation/Ubuntu).

# 1. Requirement
[Ubuntu 20.04 LTS](https://releases.ubuntu.com/focal/), [ROS Neotic](http://wiki.ros.org/noetic/Installation/Ubuntu) and [Gazebo-11](https://classic.gazebosim.org/tutorials?tut=install_ubuntu&cat=install).

# 2. Setup
Clone this repository and construct file directory.
```
    cd ~/
    mkdir catkin_ws
    cd catkin_ws
    mkdir src
    cd src
    git clone https://github.com/liuguitao/AVP-SLAM-PLUS.git
    cd AVP-SLAM-PLUS/avp_slam_plus/model/
    unzip my_ground_plane.zip -d ~/.gazebo/models/
```

# 3. Compile and build
```
    cd ~/catkin_ws
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```

# 4. Mapping
To enable map saving and utilize it for localization purposes (this repository only take RGB mode for example), it is important to ensure that your configuration file has been correctly set. The config file is located at ** avp_slam_plus/config/configFile.yaml **
```
    mapSave: true
    mapSaveLocation: your map file address (absolute path) 
```

Start mapping
```
    roslaunch avp_slam_plus slamRGB.launch
```
Open a new terminal and use keyboard to control robot
```
    chmod 777 src/Neotic-AVP-Demo/simlate_gazebo/robot_control/robot_control.py
    roslaunch robot_control robot_control.launch
```

# 5. Localization
If you have saved map as mentioned above, you can localization based on your saved map.
```
    roslaunch avp_slam_plus localizationRGB.launchv
```
Open a new terminal and use keyboard to control robot
```
    roslaunch robot_control robot_control.launch
```

## Acknowledgements
Thanks for paper [AVP_SLAM](https://arxiv.org/abs/2007.01813), and [liuguitao's implementation](https://github.com/liuguitao/AVP-SLAM-PLUS).
