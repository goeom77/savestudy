





dependencies

-JDBC api

-H2 database

-Lombok

을 넣는다.

build.gradle에

dependencies에 

```
//테스트에서 lombok사용
testCompileOnly 'org.projectlombok:lombok'
testAnnotationProcessor 'org.projectlombok:lombok'
```

을 넣어준

repository 는 dependency들을 다운 받는 url이라고 할수 있다.

logging : logback, slf4j로 사용한다.

