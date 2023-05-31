기본적으로 docker에 우분투를 설치해야한다.

순서 

1. docker설치

   파워셸에서
   docker version
   docker search
   docker pull ubuntu -> 안된다면 wsl --install -> wsl --set-default-version 2

2. wsl2 설치

3. 우분투 설치

참고 : https://myjamong.tistory.com/296#google_vignette



### web RTC란?

![image-20230119095255221](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230119095255221.png)

특징

+ 사용자가 plugin을 따로 설치하지 않고 signalling을 통해 p2p서비스를 진행해주는 것

+ 사용하는것

  ```
  세션 제어 메세지 : 통신을 초기화하거나 닫고 오류를 보고
  네트워크 구성 : 외부세계에 컴퓨터의 ip주소와 포트를 파악
  미디어 기능 : 브라우저와 통신하려는 브라우저에서 처리할 수 있는 코덱과 해상도를 파악
  ```

  ### 1:N인 경우(publisher 1명)

+ create : [1->서버로] (방이름, 방 설정)

+ join : [1->서버로] (방이름, 방에서의 역할)

+ create offer : [1->서버로]  -> publish를 할수 있는 상태 -> stream상태

+ join : [2-> 서버로] (방이름, 방에서의 역할, feed) *feed: publisher의 id

+ publish[1->서버로]

+ create answer : [2-> 서버로] create offer를 받으면 start할수 있는 상태

+ start : [2->서버로] pulbisher의 stream을 볼수 있게 방송 연결

  ### 1:1인 경우(publisher 2명)

+ create : [1->서버로] (방이름, 방 설정,pin번호) *pin번호 : 비밀번호 느낌

+ join : [1->서버로] (방이름, 방에서의 역할,pin번호)

+ create offer : [1->서버로]  -> publish를 할수 있는 상태 -> stream상태

+ publish[1->서버로]

+ join : [2-> 서버로] (방이름, publisher,pin번호) 

+ create answer : [2-> 서버로] create offer를 받으면 start할수 있는 상태

+ create offer : [2-> 서버로]

+ publish[2->서버로]

+ start : [2->서버로] pulbisher의 stream을 볼수 있게 방송 연결

  WebRTC

  ![image-20230119111338672](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230119111338672.png)

![image-20230119112042460](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230119112042460.png)

stun 동작원리 : Stun 서버를 통해 자신의 Public Address를 알아내고 접근 가능 여부를 알아낸다. Relay server은 symmetic NAT 제한을 우회하는 방식 - 이 방식은 오버헤드가 발생하므로 보안에 위험이 있기 떄문에 대안이 없을 경우에만 사용

순서 

1. 우선 각각의 peer들은 STUN 서버에 자신의 Public Address와 접근 가능한지 여부를 전달받는다
2. Peer1이 createOffer를 통해 먼저 자신의 SessionDescription을 생성하고 Signaling Server를 통해 Peer2에게 전달한다. (해당 그림에서는 Peer1이 위 그림의 Caller 역할이므로)
3. Peer2가 Peer1의 SessionDescription을 전달받고 이에 대한 답으로 createAnswer을 통해 자신의 SessionDescription을 생성하고 Signaling Server를 통해 Peer1에 전달한다.
4. Peer1과 Peer2 모두 자신의 SessionDescription을 생성한 후부터 자신의 ICECandidate 정보를 생성하기 시작하고 이를 각각 서로에게 전달한다.
5. 서로의 MediaStream을 peer 간 통신으로 주고받는다.
6. 만약 Peer1과 Peer2 둘 중 Symmetric NAT을 가진 Peer가 있는 경우 TURN 서버를 사용해 data relay로 연결을 진행해야 한다.

우선 추가로 설치하는 것

```
npm i express ejs socket.io 
# 종석성, 템플릿 언어, 소켓통신
npm uuid # 방에 대한 새로운 key
npm i --save-dev nodemon # 변경사항 생기면 서버를 새로 시작하지 않게 하기 위해 


```

server.js만들기

scripts : {

​		"dev-start": "nodemon server.js"

}

```
npm run dev start
```

server.js

```
const express = require('express')
const app = express()
const server = reuqire('http').Server(app)
const io = require('socket.io')(server)

app.set('view engine', 'ejs')
app.use(express.static('public'))

app.get('/',(req,res) => {
	res.render('room',{roomId:req.params.room})

})

server.listen(3000)
```



### open Vidu란?

kurento기반의 중개서버를 애플리케이션에 쉽게 추가 할수 있도록 완전한 기술스택을 제공

![image-20230119102341056](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230119102341056.png)

우선 나의 상황

vue로 부터 webRTC를 통해 spring boot와 연결하고 해당 영상을 comtomising 해야 한다.

1:n을 사용하려면 KMS(Kurento Media Server)가 필요하다

KMS

```
WEbRTC 미디어 서버이자 www 및 스마트폰 플랫폼 용 고급비디어 애플리케이션 개발을 간단하게 해주는 클라이언트 api세트
```





참고자료 : https://velog.io/@kimyunbin/Openvidu-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95-%ED%95%98%EA%B8%B0

