## Ros gazebo 세팅

<pre>
launch 파일이 있는 경우!
환경 모델 불러오기 + 시뮬레이션

0) bashrc 파일에 export TURTLEBOT3_MODEL=waffle 입력 후 저장
1) 패키지 및 노드 모두 준비
2) cmd1 - $ roscore
</pre>

<pre>
환경 모델 불러오기

3) cmd2 - $ cd 폴더, $ catkin_make, $ source ./devel/setup.bash
4) cmd2 - $ roslaunch 패키지이름 launch파일이름
</pre>

<pre>
시뮬레이션 진행

5) cmd3 - 시뮬레이션 파일에 대해 3번 과정 진행
6) cmd3 -  $ roslaunch 패키지이름 launch파일이름

* 만약 노드가 Python일 경우 chmod +x 파일이름.py 잊지 말기 
</pre>
