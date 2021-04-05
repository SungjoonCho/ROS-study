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
   

