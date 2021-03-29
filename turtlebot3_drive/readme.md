turtlebot3_drive 코드 공부

* 실행 순서
<pre>
  1. $ cd ~/catkin_ws/src/
     $ git clone -b kinetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
     $ cd ~/catkin_ws && catkin_make
     
  2. $ export TURTLEBOT3_MODEL=burger
     $ source ./devel/setup.bash 
     $ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
     
  3. 자동 시뮬레이션 - $ roslaunch turtlebot3_gazebo turtlebot3_simulation.launch
  4. rviz 시각화 - roslaunch turtlebot3_gazebo turtlebot3_simulation.launch 
  
</pre>

출처 : <https://github.com/ROBOTIS-GIT/turtlebot3_simulations/tree/master/turtlebot3_gazebo/src>
