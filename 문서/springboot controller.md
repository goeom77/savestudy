# spring 정리

1. Controller

1> **GetMapping("주소")**

localhost:8080/주소 클릭하면 그 이하 method로 들어간다.

이때 기본 형태 public Stirng helloMvc(Model model) {

​	model.addAttribute(attributeName:"name", name)

}

주소가 hello-mvc 이면 함수는 helloMvc처럼 넣는다.

모델에 @RequestParam("name")을 넣으면 **주소는 /주소?name=값** 으로 들어간다.



2> ResponseBody 

http에서 body부에 데이터를 넣어주겠다는 것 의미

public String helloString(@RequestParam("name") String name) {

​	return "hello" + name;

} // 이건 hello param을 그대로 내려둔다.



public  Hello

@GetMapping("hello-api")

@ResponseBody

@getter

@setter

public String helloApi(@RequestParam("name") String name) {

​	Hello hello = new Hello()

​	hello.setName(name);

​	return hello;

} // /hello-api?name=hello -> {"name" : "hello"}



static class Hello {

​	private String name;

} 



이게 무슨 뜻이냐?

javabeanset, property 접근 방식

객체처럼 사용하기 위해서 사용 원래는 viewreserver한테 던져주겠지만 객체가 오면 HttpMessageConverter(Json Converter, String Converter)를 통해 json파일로 보내게 된다.



저장소를 interface로 메모리모드로 만들어 둔다. -> 후에 JPA,RDB,SQL로 할지 바꿔끼울것