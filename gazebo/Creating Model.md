## Model 만들기

새 gazebo 열기 - $roslaunch gazebo_ros empty_world.launch

[Edit] - [Model Editor]


<img src="https://user-images.githubusercontent.com/80872528/113833318-7e1ac580-97c4-11eb-8d70-993648f4a8ff.png" width="500">

<pre>
- 몸체
  visual - geometry에서 x, y, z 값 수정. ex) (5, 1, 1) 정도로 함
  collision도 동일하게 수정해야 한다. visual은 그래픽 외형적인 모습을 바꿔주는 것뿐이고 collision이 실제 물리적인 외형을 담당하고 있다.
  color 수정은 rgba에서 0~1 값 중 하나로 수정


- 바퀴
  pose 에서 roll 1.5707로 하면 90도 누움
  visual - geometry에서 radius와 length 수정 ex) (0.5, 0.25) 정도로 함
  collision도 동일하게 수정해야 한다. 


-joint
  몸체랑 바퀴를 이어야 한다.
  몸체를 클릭 후 joint 그림을 클릭한다. Parent는 몸체로, child는 연결하고자 하는 바퀴로 설정한다. 
  Align links가 중요한데, xyz를 이용해 바퀴를 몸체의 어디에 붙일지 정해줘야 한다. 옵션은 min, max, center가 있으며 x를 min으로 해줄 경우 말 그대로 몸체에서 
  x값이 제일 작은 부분에 바퀴가 오도록 해준다. 그리고 reverse를 이용하여 바퀴가 몸체 밖으로 나오도록 만들어준다. 이 원리들을 이용해 4개의 바퀴를 몸체와 연결해주면 된다.


-저장
  File - Save as : 저장
  File - Exit model editor : 에디터 나옴
 
</pre>

- 다 저장 후 모델 수정 원하면

 모델 오른쪽 클릭 후 edit model

- Gazebo 새로 켜서 만든 모델 불러오고 싶으면

  Insert - 불러오고 싶은 모델 파일 찾아서 더블 클릭

