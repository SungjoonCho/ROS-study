## 작업 환경 만들기              
              
![image](https://user-images.githubusercontent.com/80872528/113115954-ece9a300-9247-11eb-856e-7fc07daa2309.png)
 
gazebo 폴더 내부 파일은 모델에 대한 정보, catkin_ws 내의 파일들은 모델을 gazebo로 불러오고 제어하기 위한 파일들



## model
/usr/share/gazebo-9/models 폴더 아래에 model.sdf(.urdf로 해도 됨), model.config 만들기 

config 파일 : gazebo랑 sdf 연결

## world
world 폴더 아래에 world이름.world 만들기

world에 model 올려놓으려면 model 정보 include 시키기 

단, 내가 만든 model은 /usr/share/gazebo-9/models 폴더 아래에 있어야 함


<p>    <include>
        <uri>model://모델명</uri>
    </include>
</p>


## plugin 

-> .cc : C++ 형태의 PlugIn의 동작이 들어있는 파일 (src 안에 위치시키기)

-> CMakeLists.txt : .cc 파일을 컴파일 하기위한 정보

-> launch
<pre>
<include file="$(find gazebo_ros)/launch/empty_world.launch">
아무것도 존재하지 않는 빈 공간의 Gazebo가 실행된다.
  
<arg name="paused" default="true"/>
gazebo 실행 시 정지 상태로 시작

<arg name="world_name" value="$(find ex_urdf)/worlds/house.world"/>
world 파일을 gazebo에 띄우겠다는 뜻
</pre>


출처 : <https://ola-page.tistory.com/2?category=941378>

출처 : <https://blog.naver.com/PostView.nhn?blogId=ghoism51&logNo=221439720951&parentCategoryNo=&categoryNo=23&viewDate=&isShowPopularPosts=true&from=search>

