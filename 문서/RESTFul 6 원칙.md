RESTFul 6 원칙

1. client - server 구조 : 클라이언트와 서버는 서로 독립적이다.

   클라이언트는 urls 리소스만 알아야한다.

2. stateless : 클라이언트의 모든 요청에는 해당 req를 이해할수 있는 모든 정보가 포함되어야 한다.

3. cacheable : 서버는 response cache-control 해더에 해당 요청이 케싱이 가능한 지에 대한 여부를 제공해야된다.

4. uniform interface : 규격화 - 누가 봐도 이해할수 있어야한다. 보편적인 소프트웨어 엔지니어링 원칙에 적용하면 전체적인 시스템 아케텍처는 단순화가 되고 각 상호작용에 대한 가시성이 허용

5. lay



RESTFul 7 NamingRule

1. 소문자를 사용한다.
2. 언더바를 대신 하이픈을 사용한다.
3. 마지막에 슬레시를 포함하지 않는다.
4. 행위는 포함되지 않는다.
5. 파일 확장자는 url에 포함시키지 않는다.
6. {optinal} 가ㅈ급적 전달하고자하는 자원의 명사를 사용하되 컨트롤 전원을 의미하는 경우 예외적으로 동사를 허용한다.
7. URI에 작성되는 영어는 복수형으로 작성



무료로 이용할 수 있으니 데이터 수집기들

데이터 인프라를 설치하는 사람

kibana

elasticsearch : 데이터가 많아도 생각보다 빨리나온다.

logstash

beats