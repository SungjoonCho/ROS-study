## Gazebo Model sdf,urdf 태그 정리

* sdf와 urdf 차이
 
  urdf(Unified Robot Description Format) : ROS에서 사용되는 로봇 기술(Description) 형식 

* URDF(Unified Robot Description Format) vs SDF(Simulation Description Format)

    URDF는 하나의 robot 모델에 대해 기술하는 양식. 시뮬레이션 world 상에서 robot의 pose를 결정할 수 없다.

    SDF는 world 상에서 여러개의 robot 모델에 대해 pose를 정의할 수 있으며 모델←→센서←→ World 의 관계에 대한 속성 정의도 가능하다.

    쉽게 말해 서빙 로봇 서비스가 있는 매장에서 URDF는 서빙 로봇 하나의 도면, SDF는 매장 전체 시스템의 도면

---

* Link : 로봇을 구성하는 하나의 요소
* Joint : 링크와 링크를 연결하는 요소

>태그
* visaul : 시각화 속성 & 외형 제작, 3D 도면 파일 연결 가능
* collision : 충돌 방지나 시뮬레이션에서 충돌 요소에 대한 시뮬레이션
* inertial : 링크에 대한 관성 정보

>Joint 타입

* origin : 부모 링크에서 자식 링크에 관한 변환 정보
* parent : 부모 링크 이름
* child : 자식 링크 이름

>예시 urdf 코드
<p>
<?xml version="1.0"?>
<robot name="ex_urdf_pan_tilt">

    <link name="base_link">
        <visual>
            <geometry>
                <cylinder length="0.01" radius="0.2"/>
            </geometry>
            <origin rpy="0 0 0" xyz="0 0 0"/>
            <material name="yellow">
                <color rgba="1 1 0 1"/>
            </material>
        </visual>

        <collision>
            <geometry>
                <cylinder length="0.03" radius="0.2"/>
            </geometry>
            <origin rpy="0 0 0" xyz="0 0 0"/>
        </collision>

        <inertial>
            <mass value="1"/>
            <inertia ixx="1.0" ixy="0.0" ixz="0.0" iyy="1.0" iyz="0.0" izz="1.0"/>
        </inertial>
    </link>

    <joint name="pan_joint" type="revolute">
        <parent link="base_link"/>
        <child link="pan_link"/>
        <origin xyz="0 0 0.1"/>
        <axis xyz="0 0 1" />
        <limit effort="300" velocity="0.1" lower="-3.14" upper="3.14"/>
        <dynamics damping="50" friction="1"/>
    </joint>

    
</robot>
</p>

---

xacro = xml + macro

robot description 같은 긴 xml 파일을 짧게 만들어주는데 적합 


---



>error 해결 방안

* check_urdf pan_tilt.urdf 하기 위해서는 sudo apt install liburdfdom-tools 필요
* rviz에서 [Fixed Frame]은 base_link로 설정
* gazebo 하다가 process die 에러 날 경우 - $killall gzserver $killall gzclient 
 
