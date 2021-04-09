## Realsense에서 촬영한 pointcloud 영상을 rviz에 띄우기

### terminal 1
$ roscore

### terminal 2
$ mkdir -p ~/catkin_ws_d435i/src
$ cd ~/catkin_ws_d435i/src/
$git clone https://github.com/IntelRealSense/realsense-ros.git
$catkin_init_workspace
$cd ..
$catkin_make
$source ./devel/setup.bash

$ roslaunch realsense2_camera rs_camera.launch filters:=pointcloud

### terminal 3
$ rosrun rviz rviz

Fixed Frame - camera_color_frame

[Add] - PoinCloud2

topic - /camera/depth/color/points
