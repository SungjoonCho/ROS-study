### 패키지
 - 노드, 라이브러리, 환경설정 파일 모두 통합하는 최소 빌드 단위

ROS_개념

### 노드 : 실행 가능한 프로그램  
   - 노드끼리 메시지 통신

### 패키지 노드 전체 구조 설정

* 전체구조

<img src="https://user-images.githubusercontent.com/80872528/112789901-1d3f0f00-9099-11eb-83a6-74ba4ebd43e7.png" width="500">

<pre>
1.프로젝트 폴더 만들기 - mkdir 프로젝트명

2.폴더로 이동 – cd 폴더명

3.src 만들기 – mkdir src

4.src로 이동 – cd src

5.작업 공간 만들기 – catkin_init_workspace

6.cd .. 

7.빌드 – catkin_make
</pre>
<img src="https://user-images.githubusercontent.com/80872528/112790131-9cccde00-9099-11eb-928c-5c887677f20f.png" width="500">


<pre>
8. Qt creater 열고 새 프로젝트 만들기

9. 패키지 폴더(프로젝트) 만들기 – 1번에서 만든 프로젝트 폴더와 연결

    Ros workspace 선택 후 name 설정, build system = CatkinMake,browse는 1번에서 설정한 폴더로 설정

10. 패키지 만들기

    왼쪽 프로젝트 메뉴바에서 src 우클릭 – Add new – ROS – Package

    name 설정, Catkin = roscpp, rospy (노드 언어 선택해서 쓰기)

11. 노드 만들기

    프로젝트 메뉴바에서 <폴더명> 하위 src 우클릭 – Add new – ROS – basic Node

    name 설정

12. CMakeLists.txt에 코드 추가 후 ctrl + b 빌드 , 노드 코드 입력

13. 새 터미널에서 프로젝트 폴더 들어온 후 roscore

14. 새 터미널에서 프로젝트 폴더 들어온 후 source ./devel/setup.bash

    (필요시)각 노드 chmod +x 노드명

    rosrun 패키지명 노드명

</pre>





### 메시지 : 메시지를 통해 노드 간의 데이터 주고 받음

   - 형식) integer, float, Boolean, 배열, 데이터 구조 등

   - publisher (talker) -> subscriber(listener) 메시지 전송



### yaml, rosparam

   yaml 파일은 Ros parameter server에서 쓰이는 node 구성 파라미터를 불러온다.
   
   ```cmd
   rosparam load my_cfg.yaml
   ```

   rosparam load [파일 이름]은 파일에 저장된 파라미터를 불러온다.

   ```html 
   < rosparam command="load" file="$(find my_pkg)/my_cfg.yaml" / > 
   ```

   위와 같이 launch file 내에서도 쓸 수 있다. yaml 파일을 불러온 다음에는 
   
   ```C++
   ros::NodeHandle nh;
   double rate;
   nh.getParam("node_rate" , rate);
   ```
   
   
   노드에서는 위와 같이 특정 파라미터 이름을 언급하여 매칭된 파라미터 값을 읽어와 변수에 저장할 수 있다. 여기서는 rate에 저장했다.
   
### Roslaunch

<launch> 태그 안에는 roslaunch 명령어로 노드를 실행할 때 필요한 옵션들을 적으면 된다.

* 옵션

<pre>
pkg : 패키지 이름
type : 실제 실행할 노드 이름
name : type에 해당하는 노드가 실행될 때 붙여지는 이름
</pre>

* 태그
<pre>
node : 노드 실행에 대한 태그
machine : 노드를 실행하는 pc의 이름
include : 다른 launch 파일을 불러와 현재 launch 파일과 함께 실행
param : 파라미터 이름, type, 값 설정
arg : launch 파일 내에 변수 정의 가능
</pre>

> 예시

```html
<launch>

  <!-- these are the arguments you can pass this launch file, for example paused:=true -->
  <arg name="paused" default="false"/>
  <arg name="use_sim_time" default="true"/>
  <arg name="gui" default="true"/>
  <arg name="headless" default="false"/>
  <arg name="debug" default="false"/>

  <!-- We resume the logic in empty_world.launch -->
  <include file="$(find gazebo_ros)/launch/empty_world.launch">
    <arg name="debug" value="$(arg debug)" />
    <arg name="gui" value="$(arg gui)" />
    <arg name="paused" value="$(arg paused)"/>
    <arg name="use_sim_time" value="$(arg use_sim_time)"/>
    <arg name="headless" value="$(arg headless)"/>
  </include>

  <!-- Load the URDF into the ROS Parameter Server -->
  <param name="robot_description" command="$(find xacro)/xacro --inorder '$(find ex_urdf)/urdf/pan_tilt.xacro'" /> 

  <!-- Run a python script to the send a service call to gazebo_ros to spawn a URDF robot -->
  <node name="urdf_spawner" pkg="gazebo_ros" type="spawn_model" respawn="false" output="screen"
    args="-urdf -model ex_urdf_pan_tilt -param robot_description"/> 


</launch>
```
