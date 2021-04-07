## Realsense에서 촬영된 영상 띄우기

* Develop Enviromnet

  Camera : Realsense Depth Camera D435i

  OS : Ubuntu 18.04
  
  ROS Version : melodic


* Realsense 설치

  참고 : https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md 


* Setting & Run

  1. Setting 방법 - https://github.com/SungjoonCho/ROS-study 참고
  
      Workspace : ros_opencv_realsense

      Package : ros_realsense_opencv_tutorial

      dependency : cv_bridge roscpp

   2. src, CMakeLists.txt, package.xml 다운로드 받아서 패키지 폴더 안에 넣기

   3. workspace로 돌아와서 $source ./devel/setup.bash

   4. Build - $catkin_make

   5. 실행 - $rosrun ros_realsense_opencv_tutorial ros_realsense_opencv_tutorial\


  참고 : https://www.youtube.com/watch?v=Xg472tPMs6U
