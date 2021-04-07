* 로봇 팔은 본인의 위치에서 상대적인 위치로 동작


  ROS에서는 쿼터니언(quaternion) 형태의 x,y,z,w 이용

  x,y,z는 벡터 , z는 스칼라 의미


  x,y,z 성분은 항상 동시에 변화한다. (오일러 각은 어떤 회전축이 먼저 움직일지  우선 순위를 정해줘야 한다.)

  짐벌락 문제가 없다. (짐벌락 : 두개의 짐벌이 겹쳐져서 회전축 1개가 사라지는 현상)

  (오일러 각에 비해) 계산하는데 비용이 적다.


* subscribe 한 메시지에서 값 읽어오기

  msg -> pose.pose.orientation.x

  msg -> pose.pose.orientation.y

  msg -> pose.pose.orientation.z

  msg -> pose.pose.orientation.w
