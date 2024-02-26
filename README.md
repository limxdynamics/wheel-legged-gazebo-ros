# wheel-legged-gazebo-ros 仿真使用说明


## 1. 环境搭建

- 安装Ubuntu 20.04 桌面操作系统

- 按此链接安装ROS：http://wiki.ros.org/noetic/Installation/Ubuntu，选择“ros-noetic-desktop-full”进行安装

- 按以下shell命令安装其它依赖：

  ```
  sudo apt-get update
  sudo apt install ros-noetic-hector-sensors-description -y
  sudo apt install ros-noetic-joint-trajectory-controller -y
  sudo apt install ros-noetic-urdf* -y
  sudo apt install ros-noetic-robot-* -y
  sudo apt install ros-noetic-controller-* -y
  sudo apt install ros-noetic-gazebo-* -y
  sudo apt install ros-noetic-ros-control -y
  sudo apt install ros-noetic-ecl-threads -y
  sudo apt install ros-noetic-hector-gazebo-plugins -y
  sudo apt install ros-noetic-velodyne-simulator -y
  sudo apt install ros-noetic-velodyne-description -y
  sudo apt install cmake build-essential libpcl-dev libeigen3-dev libopencv-dev libmatio-dev -y
  sudo apt install python3-pip libboost-all-dev libtbb-dev liburdfdom-dev liborocos-kdl-dev -y
  ```

  

## 2、编译

```
cd wheel-legged-gazebo-ros
catkin_make install
```



## 3、运行

- 运行`wheel-legged-gazebo-ros`仿真的同时，还需要运行一个基于`limxsdk-for-lowlevel`实现的运动控制算法程序。仿真运行流程如下图所示。

![](doc/img.png)

- 开启一个终端：运行仿真

  ```
  source /opt/ros/noetic/setup.bash
  source install/setup.bash
  roslaunch wheel_legged_robot_description empty_world.launch
  ```

- 开启一个终端：复位仿真机器人

  ```
  source /opt/ros/noetic/setup.bash
  source install/setup.bash
  roslaunch wheel_legged_robot_description reset_pose.launch
  ```

- 开启另一个终端：运行一个基于`limxsdk-for-lowlevel`实现的运动控制算法程序

  ```
  limx@limx:~/limxsdk-for-lowlevel/build$ ./examples/wl_standup
  ```
- 运行效果如下：
  <video src="doc/simulator.mkv"></video>
