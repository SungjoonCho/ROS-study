## Realsense에서 촬영된 영상 띄우기

* 일반적인 opencv 방식으로는 진행 불가능

  <pre>
  1. 시작하기 전 준비 사항
      melodic 설치 완료, SDK 2.0 설치 완료

  2. D435i camera를 컴퓨터에 usb cable로 연결

  3-1. 문제 발생 : 일반적인 노트북 캠 + OpenCV 사용 코드로 실행 불가
        -> VideoCapture(0)의 숫자를 외장 캠이라고 1로 수정해도 실행 X
        -> assertion failed error : 읽으려는 영상의 위치가 정확하지 않아서 발생

  3-2. 해결 : realsense sdk 영상을 cv::Mat으로 읽어와 while문으로 프레임 보여주기

  </pre>


* Develop Enviromnet

  Camera : Realsense Depth Camera D435i

  OS : Ubuntu 18.04
  
  ROS Version : melodic


* Realsense 설치

  참고 : https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md 


* Setting & Run
  <pre>
  1. Setting 방법 - https://github.com/SungjoonCho/ROS-study 참고
  
      Workspace : ros_opencv_realsense

      Package : ros_realsense_opencv_tutorial

      dependency : cv_bridge roscpp

   2. src, CMakeLists.txt, package.xml 다운로드 받아서 패키지 폴더 안에 넣기

   3. workspace로 돌아와서 $source ./devel/setup.bash

   4. Build - $catkin_make

   5. 실행 - $rosrun ros_realsense_opencv_tutorial ros_realsense_opencv_tutorial
  </pre>

  참고 : https://www.youtube.com/watch?v=Xg472tPMs6U
