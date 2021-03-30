## Gazebo Model urdf 개념

<p>
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
</p>

visaul : 외형 제작, 3D 도면 파일 연결 가능
collision : 충돌 방지나 시뮬레이션에서 충돌 요소에 대한 시뮬레이션
inertial : 관성

<해결>

check_urdf pan_tilt.urdf 하기 위해서는 sudo apt install liburdfdom-tools 필요

rviz에서 [Fixed Frame]은 base_link로 설정

gazebo 하다가 process die 에러 날 경우 - $killall gzserver $killall gzclient 
 
