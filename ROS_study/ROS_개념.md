### 패키지
 - 노드, 라이브러리, 환경설정 파일 모두 통합하는 최소 빌드 단위

### 노드 : 실행 가능한 프로그램  
   - 노드끼리 메시지 통신

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
