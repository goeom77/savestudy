CI/CD

속성 

```
--name : 컨테이너 생성
-p : 내부 포트 지정
-d : 데몬으로 백그라운드 실행
--restart always : 재부팅시 서비스 자동 시작
-v /data : 호스트와 도커 컨테이너간 볼륨 매칭
```



sudo docker status : docker의 관계 보여줌

### nginx

ddos 공격에도 편리

비동기 html에 있어서 효율 상승

일부 고장이 나면 원하는 화면을 띄워줄수 있다.

```
ps aux --forest : 부모 자식간의 상관관계

nginx : include를 통해 설정 파일 관리
```



### nginx proxy manager

- 기본적인 포워드 프록시와 역방향 프록시에 대한 이해 필요

e) 도메인 관리, 

host 연결을 하다가 internal error 발생한 경우

root계정으로 nginx proxy manager에 들어가서 

```
grep -Ri "/acme/authz" /var/log/letsencrypt/* | curl -m60 --data-binary @- https://letsdebug.net/_/003567432e
```

를 입력한다.

![image-20230205100200266](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230205100200266.png)

다음과 같은 화면 이후 10분뒤 internal error는 없어진다.



공부 참고 : https://it-svr.com/synology-reverse-proxy-nginx-proxy-manager/

### portainer

효율적인 네트워크 관리,

전반적인 흐름을 설명하는데도 유리

기본적인 cnf파일을 관리해 줌으로써 깔끔한 docker관리 가능

