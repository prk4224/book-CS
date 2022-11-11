# MVC 패턴

*모델(Model), 뷰(View), 컨트롤러(Controller)로 이루어진 디자인 패턴*

![Untitled](https://user-images.githubusercontent.com/48992412/197216411-09f02f36-48df-4f74-b45b-e8467d2c85b9.png)

- 애플리케이션의 구성 요소를 세 가지 역할로 구분
- 개발 프로세스에서 각각의 구성 요소에만 집중해서 개발 가능
- 재사용성과 확장성이 용이하다는 장점
- 애플리케이션이 복잡해질수록 모델과 뷰 관곅 복잡해지는 단점

### Model

모델(model)은 애플리케이션의 데이터인 데이터베이스, 상수, 변수 등을 뜻한다.

### View

View 는 사용자 인터페이스 요소를 나타낸다. 즉 모델을 기반으로 사용자가 볼 수 있는 화면을이고,최근에는 react, vue, svelte 와 같은 프론트 프레임워크로 구성된다.

### Controller

컨트롤러(controller)는 하나 이상의 모델과 하나 이상의 뷰를 잇는 다리 역할을 하며 이벤트 등 메인 로직을 담당한다. 또한, 모델과 뷰의 생명주기도 관리하며, 모델이나 뷰의 변경 통지를 받으면 이를 해석하여 각각의 구성 요소에 해당 내용에 대해 알려준다.

### MVC 패턴 방식

MVC 패턴에는 모델 1 방식과 모델 2 방식이 있는데

- **모델 1 방식: JSP에서 출력과 로직을 전부 처리**
- **모델 2 방식: JSP에서 출력만 처리**

로 분류할 수 있습니다.

- 모델 1

![Untitled 1](https://user-images.githubusercontent.com/48992412/197216399-af5733c1-fb5a-4f8a-bb22-47fd5ef9cdf8.png)

모델 1 방식은 Controller 영역에 View 영역을 같이 구현하는 방식이며, 사용자의 요청을 JSP가 전부 처리합니다. 요청을 받은 JSP는 JavaBean Service Class를 사용하여 웹브라우저 사용자가 요청한 작업을 처리하고 그 결과를 출력합니다.

- 모델 2

![Untitled 2](https://user-images.githubusercontent.com/48992412/197216409-b9e1d0f9-870d-43fb-b7a7-dfa67e5639cc.png)

모델 2 방식은 웹브라우저 사용자의 요청을 서블릿이 받고 서블릿은 해당 요청으로 View로 보여줄 것인지 Model로 보낼 것인지를 판단하여 전송합니다. 또한 모델 2 방식의 경우 HTML 소스와 JAVA소스를 분리해놓았기 때문에 모델 1 방식에 비해 확장시키기도 쉽고 유지보수 또한 쉽습니다.

 **Model 1 방식으로 웹서비스를 개발하는 사례는 백엔드와 프론트엔드의 역할 분담이 모호해져 협업이 쉽지 않으며 실제 서비스들 중에서 거의 없다고 봐도 무방합니다.**

### MVC 패턴을 사용하는 라이브러리

- **React**
- **Angular JS**
- **django**

## REFERENCE

MVC 패턴이란? - [https://cocoon1787.tistory.com/733](https://cocoon1787.tistory.com/733)

### 참고자료

****스프링 MVC - 구조 이해****- [https://catsbi.oopy.io/f52511f3-1455-4a01-b8b7-f10875895d5b](https://catsbi.oopy.io/f52511f3-1455-4a01-b8b7-f10875895d5b)

Spring MVC 용어 - [https://m.blog.naver.com/jysaa5/221751719334](https://m.blog.naver.com/jysaa5/221751719334)
