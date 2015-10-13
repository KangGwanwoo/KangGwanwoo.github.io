---
layout: post
title: MVC와 DispatcherServlet
---

DispatcherServlet 이란 ?
----------------------------------
---

- 해당 어플리케이션으로 들어오는 요청을 모두 **핸들링하는 객체**

- web.xml와 **상호 작용**하는 객체

web.xml은 web application의 deployment descriptor로서 xml 형식의 파일인데,

이 web.xml에서 가장 주요한 기능인 servlet 매핑을 DispatcherServlet으로 넘겨줄 수 있습니다.

서블릿 매핑은 어떤 URL로 들어오는 요청에 대해서 어떠한 서블릿을 실행시킬 것인가에 대한 얘기인데, 이 설정을 web.xml에서 하나하나 하기 보다는 

Spring 프로젝트에서는 web.xml에서 DispatcherServlet의 '<'url-pattern'>'을 ‘/‘로 설정하면 이 서블릿 매핑을 스프링, 즉 DispatcherServlet에게 위임 할 수 있습니다.

또 DispatcherServlet을 web.xml에 설정 한다는 것은 스프링에서 제공하는 **@MVC**를 이용하겠단 뜻이 될 수 있는데,

여기서 MVC 패턴이란 무엇일까요 ?

###@MVC 패턴
---
MVC란 Model View Controller의 약자로 하나의 어플리케이션을 세가지의 역할로 구분한 개발 방법론입니다.

아래의 그림처럼 사용자가 Controller를 조작하면 Controller는 Model을 통해서 데이터를 가져오고 그 정보를 바탕으로 시각적인 표현을 담당하는 View를 제어해서 사용자에게 전달하게 됩니다.

<br>
![mvc model](/public/MVC.png)
<br>

[출처:생활코딩](https://opentutorials.org/course/697/3828)

---

DispatcherServlet에 대해 간단히 정의해보자면 우리가 각각 분리하여 만든 MVC각 파트를 조합하여 브라우저로 출력해주는 역할을 수행하는 클래스라고 할 수 있습니다.

<br>
![dispatcher](/public/spring_dispatcher.png)
<br>

< UML 스타일 DispatcherServlet 작동 방식 >
---
위의 작업 흐름을 풀어 설명하자면 다음과 같습니다.

①  클라이언트가 해당 어플리케이션에 접근하는 URL 요청을 DispatcherServlet이 가로챕니다. 이렇게 요청을 가로챌 수 있는 이유는 web.xml에 등록된 DispatcherServlet의 <url-pattern>이 ‘/‘와 같이 해당 어플리케이션의 모든 URL로 등록되있기 때문입니다. 만약 여러 개의 어플리케이션이 올라가거나 해서 특정 URL만 적용하고 싶다면 <url-pattern>의 내용을 바꿔주어 범위를 변경시켜주면 됩니다.

② 가로챈 정보를 HandlerMapping에게 보내 해당 요청을 처리할 수 있는 Controller를 찾아냅니다. 이 핸들러들은 5가지 정보 클래스로 스프링에서 구현되어 있는데, 기본적으로 BeanNameUrlHandlerMapping과 DefaultAnnotationHandlerMapping이 설정 되어 있습니다. 그 외 클래스를 핸들러 매핑으로 사용하려면 핸들러 매핑 클래스를 빈으로 등록해주셔야 됩니다. 자세한 내용은 [신관영님 블로그](http://springsource.tistory.com/3)에서 공부 하실 수 잇습니다.
제가 자주 사용하는 DefalutAnnotationHandlerMapping에 대해서 간단히 설명하자면
@RequestMapping이라는 애노테이션을 컨트롤러 클래스나 메소드에 직접 부여하고 이를 이용해 매핑하는 전략입니다.
이는 메소드 단위로도 URL 을 매핑해 줄 수 있어서 컨트롤러의 개수를 획기적으로 줄일 수 있다는 점, URL마다 HTTP 메서드 정보와 파라메터, 헤더정보를 나누어 매핑할 수 있다는 장점이 있지만 매핑 애노테이션의 사용정책과 작성 기준을 잘 만들어 두지 않으면, 개발자 마다 제멋대로 매핑방식을 적용해서 매핑정보가 지저분해지고 관리하기 힘들어 질 수 있다는 단점이 습니다.

③ 핸들러 매핑이 해당 요청을 처리할 컨트롤러를 찾아냈다면 요청을 컨트롤러에 보내줍니다. 컨트롤러는 사용자가 직접 구현해주는 부분입니다.

④ 컨트롤러가 해당 요청(비지니스 로직)을 처리한 후 반환한 모델(데이터)들을 View에 리턴해주기 위해 View이름을 DispatcherServlet으로 전송합니다.

⑥ 해당 View가 있다면 처리결과를 View에 보낸 후 ⑦ 이 결과를 다시 DispatcherServier에 보낸 후 ⑧ DispatcherServlet은 최종 결과를 클라이언트에 전송합니다.



#### DispatcherServlet이 모든 URL 가로채서, 컨트롤러에 넘겨주어도 괜찮을까요 ?

만약 이렇게 모든 요청을 가로채버린다면, 이미지나 HTML 파일을 불러오는 요청마저 전부 컨트롤러를 찾는 로직이 실행되기 때문에 제대로 **자원을 불러올 수 도 없는 상황**이 생깁니다.

이 문제에 대해서 스프링은 편리한 해결방법을 고안해 냈습니다.
~~~xml
<resources mapping="/resources/-'*'" location="/resources/" /> 
~~~

~~~xml
<mvc:resources /> 
~~~
태그를 활용하는 전략을 취해서 , 먼저 디스패처 서블릿을 통해 들어온 요청을 처리하는데 만약 디스패처 서블릿이 해당 요청에 대한 컨트롤러를 찾을 수 없다면 2차적으로 위의 설정된 경로를 검색해여 해당 자원을 찾아내게 합니다.

이 방법을 통해서 비 어플리케이션 자원을 철저하게 분리하는게 가능해졌습니다.

이로써 DispatcherServlet에 대한 내용을 MVC 기반으로 작성하였습니다.

[필명 거짓말](http://egloos.zum.com/springmvc/v/504151) 님의 포스트를 그대로 옮겼다고 볼 수 있는데, 이 포스트로 공부를 하고 블로그에 정리를 하다보니 자연스럽게 그렇게 되네요 ㅎㅎ

이 포스트를 보고 이해가 안되는게 있다면 저에게 페북 메세지를 주시거나, 위 원본 포스트를 참고하시길 바랍니다.
 