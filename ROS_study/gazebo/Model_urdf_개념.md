## Gazebo Model urdf 개념

>패키지 생성
1. 폴더 생성
2. src 생성 후 들어가기
3. $ catkin_create_pkg ex_urdf roscpp tf geometry_msgs urdf rviz xacro
4. src 내에 launch, urdf 폴더 생성
5. src 나와서 catkin_make


>개념

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

    <link name="pan_link">
        <visual>
            <geometry>
                <cylinder length="0.4" radius="0.04"/>
            </geometry>
            <origin rpy="0 0 0" xyz="0 0 0.09"/>
            <material name="red">
                <color rgba="0 0 1 1"/>
            </material>
        </visual>

        <collision>
            <geometry>
                <cylinder length="0.4" radius="0.06"/>
            </geometry>
            <origin rpy="0 0 0" xyz="0 0 0.09"/>
        </collision>

        <inertial>
            <mass value="1"/>
            <inertia ixx="1.0" ixy="0.0" ixz="0.0" iyy="1.0" iyz="0.0" izz="1.0"/>
        </inertial>
    </link>

    <joint name="tilt_joint" type="revolute">
        <parent link="pan_link"/>
        <child link="tilt_link"/>
        <origin xyz="0 0 0.2"/>
        <axis xyz="0 1 0" />
        <limit effort="300" velocity="0.1" lower="-4.71239" upper="-1.570796"/>
        <dynamics damping="50" friction="1"/>
    </joint>

    <link name="tilt_link">
        <visual>
            <geometry>
                <cylinder length="0.4" radius="0.04"/>
            </geometry>
            <origin rpy="0 1.570796 0" xyz="0 0 0"/>
            <material name="green">
                <color rgba="1 0 0 1"/>
            </material>
        </visual>

        <collision>
            <geometry>
                <cylinder length="0.4" radius="0.06"/>
            </geometry>
            <origin rpy="0 1.570796 0" xyz="0 0 0"/>
        </collision>

        <inertial>
            <mass value="1"/>
            <inertia ixx="1.0" ixy="0.0" ixz="0.0" iyy="1.0" iyz="0.0" izz="1.0"/>
        </inertial>
    </link>
    
</robot>
</p>



<해결>

check_urdf pan_tilt.urdf 하기 위해서는 sudo apt install liburdfdom-tools 필요

rviz에서 [Fixed Frame]은 base_link로 설정

gazebo 하다가 process die 에러 날 경우 - $killall gzserver $killall gzclient 
 
