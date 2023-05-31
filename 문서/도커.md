DevOps해야하는 이유

도커와 쿠버네티스가 무엇인가?

![image-20230106140455080](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106140455080.png)

![image-20230106140545719](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106140545719.png)

![image-20230106140630121](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106140630121.png)

ㅁ 따로 기능을 나누기

![image-20230106140723639](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106140723639.png)

ㅁ마지막으로 사용자가 많이 없을 때는 괜찮더라도 사람이 많아지면 모니터링이 중요해진다. 

aws에서 서버 운영 너무 쉽넹



![image-20230106142311201](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106142311201.png)

![image-20230106142811115](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106142811115.png)

![image-20230106142846899](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106142846899.png)

가상머신을 만들어두면 쉬워진다. 한개당 40기가 저장,

4. 클라우드

![image-20230106143041089](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106143041089.png)

5. PaaS

![image-20230106143140655](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106143140655.png)

단점 : 일반화된 프로비저닝 방법을 제공(맞춰진 틀에 따라 만들어짐)

화면에서 클릭만 하고 -> 직접들어가서 컨트롤 할수 없다.

파일 시스템을 사용할 수 없다.



파스로 운영을 하다가 -> 단점이 프로젝트에 문제로 여겨진다면 바꾸는 방법을 권장 



### 도커

![image-20230106144011285](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106144011285.png)

도커 : 서버를 2개로 만들어서 -> 배포의 페러다임을 바꾸기 -> 모두 컨테이너화로 관리

![image-20230106144722473](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106144722473.png)

로켓 쳇 : 실시간 대화 입력 

도커 : 2013년 첫 공개 이후 -> 하드웨어 가상화 기술을 쉽게 만들어줬다.

가상화면에 앱 위에 뒤집어 씌워 무겁다면 -> 도커는 따로 관리해서 가볍다.



도커 허브의 역할 : img는 apk파일이 있으면 설치로 만들 수 있다. -> 설치할 때 필요한 것 압 축관리

wsl쓰면 빠르게 사용할 수 있다. -> 도커 리눅스 버전



도커의 어떤 서버에 어떤 컨테이너가 비어있는지 확인 하기위해 -> 

![image-20230106151815165](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106151815165.png)

로드 벨런스를 설치하면 -> 가상 ip에 대해서 자동화시켜 바꿔준다.

이름이 다른 경우 , 자동으로 문제가 발생 했을 때 문제가 있는 서버를 표시 및 확인 할수 있게

중앙제어, 네트워크, 노드 스케일이 커도 관리 가능 , 상태 관리 

![image-20230106152303495](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152303495.png)

![image-20230106152315683](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152315683.png)

서비스 등록 및 조회, 서버 변경 -> 자동화

![image-20230106152356121](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152356121.png)

볼륨 스토리지를 자동으로 변경(쿠버네티스의 평정)

![image-20230106152639155](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152639155.png)

![image-20230106152652363](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152652363.png)

![image-20230106152730462](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230106152730462.png)