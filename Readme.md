## ROS 개념 정리

* 전체구조

![image](https://user-images.githubusercontent.com/80872528/112789901-1d3f0f00-9099-11eb-83a6-74ba4ebd43e7.png)

<pre>
1.프로젝트 폴더 만들기 - mkdir 프로젝트명

2.폴더로 이동 – cd 폴더명

3.src 만들기 – mkdir src

4.src로 이동 – cd src

5.작업 공간 만들기 – catkin_init_workspace

6.cd .. 

7.빌드 – catkin_make
</pre>
![image](https://user-images.githubusercontent.com/80872528/112790131-9cccde00-9099-11eb-928c-5c887677f20f.png)

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
