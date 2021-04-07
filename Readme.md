# ROS 개념 정리

### * develop environment

OS : Ubuntu 18.04

ROS Version : melodic

### * 전체구조 정리 및 Setting

<img src="https://user-images.githubusercontent.com/80872528/112789901-1d3f0f00-9099-11eb-83a6-74ba4ebd43e7.png" width="500"> </img>

<pre>
1.작업 공간(프로젝트명) 만들기 - $mkdir workspace_name

2.작업 공간으로 이동 – $cd 폴더명

3.src 만들기 – $mkdir src

4.src로 이동 – $cd src

5.catkin package 작성 – $catkin_create_pkg beginner_tutorials std_msgs rospy roscpp

  beginner_tutorials는 패키지 이름 , rospy과 roscpp 등은 dependencies

6.$cd .. 

7.build – $catkin_make
</pre>

### * 전체 노드 코드 및 CMakeLists 작성 후 실행
<pre>

1.새 터미널에서 workspace 들어온 후 roscore

2. 새 터미널에서 workspace 들어온 후 
   $source ./devel/setup.bash

   (노드가 파이썬일 경우)각 노드 접근 후 $chmod +x 노드명

   $rosrun 패키지명 노드명

</pre>
