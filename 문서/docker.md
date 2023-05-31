Docker

참고 : https://docs.docker.com/get-started/

구성

+ 컨테이너 : 호스트 시스템의 다른 모든 프로세스와 격리된 시스템의 샌스박스 프로세스(이미지의 실행가능한 인스턴스)
  CLI를 이용해서 생성, 시작, 중지, 이동, 삭제 가능하다.
+ 컨테이너 이미지 : 컨테이너를 실행할 때 격리된 파일 시스템을 사용합니다. 이미지에는 컨테이너의 파일시스템, 애플리케이션을 실행하는데 필요한 모든것이 포함되어야 합니다.
+ Docker File : 도커가 컨테이너 이미지를 생성하는 데 사용하는 명령 스크립트가 포함되어 있습니다.

예 ) 

```
# syntax=docker/dockerfile:1
FROM node:18-alpine // 빌더에게 이미지에서 시작하고 싶다고 지시
WORKDIR /app // 작업 위치
COPY . .
RUN yarn install --production // 애플리케이션 종속성 설치
CMD ["node", "src/index.js"] // 이미지에서 컨테이너를 시작할 때 실행하는 기본 명령
EXPOSE 3000
```

docker build -t getting-started

: 컨테이너 이미지를 빌드한다.

```
 docker run -dp 3000:3000 getting-started
```

: "분리된" 모드에서 새 컨테이너 실행(d), 플래그를 사용해 매핑을 생성(p)

```
docker ps
```

컨테이너의 id 확인

```
docker stopp <the-container-id>
```

해당 컨테이너 중지

```
docker rm <the-container-id>
```

중지된 컨테이너 제거

```
$ docker push docker/getting-started // Nope
```

push 명령은 docker/getting-started라는 이미지를 찾지만 

docker image ls하면 안뜹니다. 이를 위해 이미지에 "태그"를 지정해야합니다.

```
docker login -u Your-User-Name
```

로그인을 합니다.

```
docker tag getting-started YOUR-USER-NAME/getting-started
```

태그를 지정합니다.

이제 다시 push하면 사용가능합니다.