URI VS URL

URL : host:8080/client

URI : /client

mandantory validation : client에서 보낸것도 검증을 해줘야한다.(프론트를 믿지 않는다.)

intercept 단계에서 모두 확인해줘야한다(?) 

예외케이스, 에러를 산출해서 - > 데이터화 한다면 그때 백에서 데이터 진행

공통 에러코드를 사용할것 너무 자세하면 역추적으로 해킹의 우려가 있다.

