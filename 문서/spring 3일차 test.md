## spring 4일차

spring boot 구조 이해하기

![image-20230121134038452](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230121134038452.png)

1. src/main/java 디렉터리
   클래스, 인터페이스 등 자바 파일이 위치하는 디렉터리
2. BoardApplication 클래스

| **애너테이션**           | **설명**                                                     |
| ------------------------ | ------------------------------------------------------------ |
| @EnableAutoConfiguration | 스프링 부트는 개발에 필요한 몇 가지 필수적인 설정들의 처리가 되어 있는데요,  해당 애너테이션에 의해 다양한 설정들의 일부가 자동으로 완료됩니다. |
| @ComponentScan           | 기존의 XML 설정 방식의 스프링은 빈(Bean)의 등록 및 스캔을 위해  수동으로 ComponentScan을 여러 개 선언하는 방식을 사용하였습니다.  스프링 부트는 해당 애너테이션에 의해 자동으로 컴포넌트 클래스를 검색하고,  스프링 애플리케이션 콘텍스트(IoC 컨테이너)에 빈(Bean)으로 등록합니다.  쉽게 이야기하면, 의존성 주입 과정이 더욱 간편해졌다고 생각할 수 있습니다. |
| @Configuration           | 해당 애너테이션이 선언된 클래스는 자바 기반의 설정 파일로 인식됩니다.  스프링 4 버전부터 자바 기반의 설정이 가능하게 되었으며,  XML 설정에 어마 무시한 시간을 소모하지 않아도 됩니다.  물론, XML 기반의 설정을 전혀 사용하지 않는 것은 아닙니다. |

3. src/main/resources 디렉터리
   templates, static, application.properties 생성

| **폴더 및 파일**       | **설명**                                                     |
| ---------------------- | ------------------------------------------------------------ |
| templates              | 기존의 스프링은 HTML 내에 자바 코드를 삽입하는 방식의 JSP를 사용하였습니다.  디렉터리의 위치도 웹 디렉터리에 해당하는 src/main/webapp 안에 존재했구요.  하지만, 이러한 방식은 war 파일로 패키지화되었을 경우에만  정적 리소스를 정상적으로 사용할 수 있다고 합니다.  그러한 이유에서 스프링 부트는 src/main/resources 디렉터리 내에서  화면과 관련된 파일을 관리하는 것으로 생각할 수 있습니다.  스프링 부트는 타임리프(Thymeleaf) 템플릿 엔진의 사용을 권장하는데요,  타임리프는 JSP와 마찬가지로 HTML 내에서 데이터를 처리하는 데 사용됩니다.  우리는 이전 글에서 타임리프를 사용하기로 하였고, 관련 플러그인도 설치했습니다.  타임리프는 게시판을 구현하면서 차근차근 알아가 보도록 하겠습니다. |
| static                 | 해당 폴더에는 css, fonts, images, plugin, scripts 등의 정적 리소스 파일이 위치합니다. |
| application.properties | 해당 파일은 웹 애플리케이션을 실행하면서 자동으로 로딩되는 파일입니다.  예를 들어, 톰캣(Tomcat)과 같은 WAS(포트 번호, 콘텍스트 패스 등)의 설정이나,  데이터베이스 관련 정보 등 각각으로 분리되어 있는 XML 또는 자바 기반의 설정을  해당 파일에 Key-Value 형식으로 지정해서 처리할 수 있습니다.  마찬가지로 자세한 부분은 게시판을 구현하면서 알아가 보도록 하겠습니다. |

4. controlloer

|            패턴            |                             설명                             |
| :------------------------: | :----------------------------------------------------------: |
| 컨트롤러, Controller - (C) | 쉽게 이야기하면, 모델(M) 영역과 뷰(V) 영역의 중간 다리 역할을 하는 영역입니다.  사용자가 웹에서 어떠한 요청을 하면, 가장 먼저 컨트롤러를 경유합니다.  컨트롤러는 사용자의 요청을 처리할 어떠한 로직을 호출하고,  호출한 결과를 사용자에게 전달하는 역할을 합니다.  예를 들어, 사용자가 게시판에 게시글을 작성하고 등록을 요청하면,  컨트롤러는 게시글의 제목, 내용, 작성자, 등록일 등에 해당하는  파라미터(이하 데이터)를 전달받아 유효성을 검증합니다.  검증이 완료되면, 모델 영역에 데이터의 가공을 요청합니다.  가공이 완료되면 전달받은 데이터를 데이터베이스에 저장하고,  저장의 성공 또는 실패 여부를 컨트롤러로 전달합니다.  마지막으로 컨트롤러는 등록 요청에 대한 결과를 뷰로 전달합니다. |

![image-20230121140915443](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230121140915443.png)

![image-20230121140924590](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230121140924590.png)