## spring 2일차 MVC

종류

+ 정적 컨텐츠
+ MVC와 템플릿 엔진
+ API

접속 : controller가 없으면 바로 template으로 연동

Controller

```
@Controller
public class HelloController {
@GetMapping("hello-mvc")
public String helloMvc(@RequestParam("name") String name, Model model) {
model.addAttribute("name", name);
return "hello-template";
}
}
```

View

```
<html xmlns:th="http://www.thymeleaf.org">
<body>
<p th:text="'hello ' + ${name}">hello! empty</p>
</body>
</html>
```

API 방식

@responsebody가 있으면  viewResolver 대신 HttpMessageConverter가 작용

JsonConverter: 기본 객체 처리

StringConverter: 기본 문자 처리



## 회원가입 사이트만들기

![image-20230120121036992](C:\Users\SSAFY\AppData\Roaming\Typora\typora-user-images\image-20230120121036992.png)

domain

```
package hello.hellospring.damain;

public class Member {

    private Long id;
    private String name;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```



getter와 setter의 특징

->다른곳에서 똑같은 것을 선언하지 않도록 하기 위해서 사용





null값이 될수 있다면 return Optional.ofNullable사용

검증할 때는 test case를 사용해봐야한다.