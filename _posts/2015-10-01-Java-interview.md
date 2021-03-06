---
layout: post
title: Java 핵심 정리
---


###1. 자바의 데이터 타입인 Primitive Type과 Reference Type에 대해 설명하세요.

>자바는 자료형이 기본 자료형, 참조 자료형으로 나뉘는데 기본 자료형은 문자형,숫자형,논리형등이 있고 세세하게는 char,byte,int,long등이 있다. 자료형 이름을 보아서 알 수 있듯이 우리가 자료형이라 생각하고 선언하는 것들은 기본자료형에 속하며 앞글자가 소문자이다. 
이에 반해 참조 자료형은 String , Object등 클래스, 인터페이스, 배열이다. 객체 자료형이므로 이 들 자료형은 객체가 가질수 있는 메서드를 가지고 있다. 예를 들어 String의 trim ( 문자열의 공백을 제거 ) 를 들 수있다.


###2. 다형성이란 무엇인가 ?

>여러가지로 나타날 수 있다 라는 말로 이해하면 쉬울 것 같다. 즉 조상클래스를 여러 자손 클래스들이 상속 받아 나름대로 구현할 수 있다는 특성이다.

###3. 멀티 쓰레드의 장-단점은 무엇인가 ? 

>두 가지 이상의 작업을 동시해 실행 할 수 있어 자원을 효율적으로 이용할 수 있으나 Synchronized를 통해서 자원에 대한 동기화가 필요하다. 그렇지 않으면 임계영역 문제(생산자/소비자문제) 등이 생길 수 있다.

###4. Java 콜렉션 프레임워크에 대해서 설명하시오.

>Java에서는 자료구조에서 나오는 자료구조들을 콜렉션 프레임워크를 통해서 구현해 놓았다. 예를 들어 List,Set,Map등이 있는데, 간단히 설명하자면 List는 순서가 있는 데이터 집합으로 데이터의 중복을 허용하는 자료형이고 Set은 순서를 유지하지 않고 데이터의 중복 또한 허용하지 않는 자료형, Map은 키와 값의 쌍으로 이루어진 데이터 집합이다. 물론 키는 중복을 허용하지 않고, 값은 중복을 허용한다.
자세한 설명은 [여기](http://devbox.tistory.com/entry/Java-%EC%BB%AC%EB%A0%89%EC%85%98-%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC)에서 공부할 수 있다. 

###5. 객체의 직렬화란 무엇인가?

>객체를 데이터 스트림으로 만드는 것이다. 구현을 위해서 직렬화 하고자 하는 클래스에 Java.io.Serializable 인터페이스를 구현해야한다.

###6. 접근제어자의 종류와 특성을 설명하시오.

>private - 같은 클래스 내에서만 접근이 가능하다.

>default - 같은 패키지 내에서만 접근이 가능하다.

>protected - 같은 패키지 내에서, 그리고 다른 패키지의 자손클래스에서 접근이 가능하다.

>public - 접근 제한이 전혀 없다.

###7. Wrapper 클래스란 무엇인가 ? 

>기본 자료형을 객체로 만들때 사용하는 참조 자료형 클래스로써 대부분 기본 자료형의 앞글자를 대문자로 바꾸어 구현되어 있다.

###8. 객체 지향 언어의 장점은 무엇인가?

>코드의 재사용성과 유지보수성이 높아 새로운 코드를 작성할때 기존의 코드를 사용해서 쉽게 작성하거나, 관리가 용이하다.

###9. Thread를 구현하기 위한 두 가지 방법은 무엇인가?

>java.lang.Thread 클래스를 상속 받거나 java.lang.Runnable 인터페이스를 구현한다.

###10. 추상 클래스란 무엇인가 ?

>자손클래스를 위한 클래스 설계도라고 할 수 있다. 메서드를 정의만 해두고 구현은 자손클래스에게 맡긴다.

###11. NIO란 무엇인가 ?

>기존 자바IO의 단점을 보완한 New IO로써 논블로킹 IO를 지원함으로써 대용량 처리에 용이하다.

###12. Vector와 ArrayList 그리고 LinkedList의 차이점

>참조 자료형인 Array는 초기에 배열의 크기를 정하고 정해준 크기 이상의 인덱스를 추가하고자 하면 예외가 발생한다.반면 Vector와 ArrayList 그리고 linkedList는 동적으로 배열의 크기를 늘릴 수 있다. Vector는 내부적으로 동기화를 지원하여 데이터를 추가/삭제할때 다른 클래스가 접근하지 못하게 막아준다. 
그러므로 필연적으로 성능의 저하를 가져온다. 때문에 ArrayList는 동기화 기능을 아예 빼버렸는데, 이에 안정성에 문제가 있을 수 있으므로 사용자레벨에서 동기화를 구현해 주어야 한다. 
ArrayList라는 이름에 걸맞게 Array를 이용해서 구현되어 있으므로 이 데이터 검색에는 인덱스로 접근해서 빠르지만, 추가,삭제에서는 성능을 보장하지 못한다. 반대로 LinkedList는 데이터의 추가/삭제에서 용이하지만 검색에서는 인덱스로 접근하는 것보다 느리다.       
출처 : [http://shagall.tistory.com/36](http://shagall.tistory.com/36)

###13. OOP의 특징

>상속성,다형성,은닉성, 캡슐화가 있는데 이런 용어를 암기할려고하면 어렵다. 
그래서 이해를 해버리면 당연한 얘기 이므로 이해하는게 좋다. 
상속성은 상위 클래스를 하위클래스에서 상속해서 재사용할 수 있다는 것이다. Car라는 클래스를 만들면 Bus, Taxi등 여러 클래스에서 상속받아 Car에 drive메서드를 구현하여 사용할 수 있다는 것이다. 다형성은 이 drive라는 클래스를 bus는 50km/h로 움직인다! 하는거고 Taxi는 70km/h로 움직이다! 해서 다양~하게 구현하는 것이다. 
은닉성은 데이터의 훼손 방지를 위해서 접근제어자를 통해 데이터를 보호하는 것이고 캡슐화는 데이터와 데이터를 처리하는 함수를 하나로 묶는다는 개념인데 Gatter,Setter를 들 수 있다. 

###14. 오버로딩과 오버라이딩

>오버로딩은 같은 클래스 내에서 매개변수나 타입을 다르게 설정하여 다른 구현을 나타내는 것이다. 
오버라이딩은 상속성의 예처럼 부모클래스의 같은 이름의 메서드를 상속받은 자손클래스들이 다르게 그 메서드를 구현하는 것이다.
같은 점은 메서드이름이 같은데 다른 일을 할 수 있다는 점이다. 말이 비슷해서 헷갈릴 수 있는데 로딩이 쌓는다는 의미니까 같은 클래스에서 여러 메서드를 다른 크기로 쌓아~간다 하면 오버로딩 한 메서드가 여러 클래스에서 다른 방식으로 구현 될려면 바쁘게 움직여야 되니 말을(라이딩) 타고 왔다갔다 한다는 의미로... 기억하면 외워질거다....

###15. JVM 메모리 구조

>JVM은 크게 Method Area, 스택, heap 영역으로 나눌 수 있다.
Method Area(Class Area,Static Area)라고도 하는 이 영역은 java source에서 컴파일된 class파일들이 올라간다.
필드 정보, 메서드 정보, Static,final변수들이 이 메모리에 올라가서 관리된다.
스택 영역은 메서드 호출 시 마다 하나 씩 쌓여가며 스택에 올라가며 스택이란 메모리 구조와 마찬가지로 FILO구조를 가진다.
지역 변수들이 이 영역에 올라가서 관리된다.
힙 영역은 new 연산자로 생성된 인스턴스가 올라가며 가비지 콜렉터가 관리한다.
추가로 PC register가 있는데 Tread가 생성 될 때마다 생성되는 공간이다.


###16. 가비지 컬렉션 ( Garbage collection )

>가비지 컬렉션(GC) - null을 참조하거나 더 이상 사용하지 않는 객체에 대한 메모리를 heap영역에 반환해준다.
가비지 컬렉션은 특정 규모 이상 어플리케이션을 사용할때 GC를 직접 컨트롤해서 메모리 누수문제를 해결해야 할 것 같다.
만약 경력직 입사를 위해서 이 글을 보고 있다면, [naver blog](http://d2.naver.com/helloworld/1329) 이 글을 참조하는 것이 더 좋을 것 같다.
	
	
**자바** 신입 (JAVA) 프로그래머들을 위한 면접 대비 질문들을 뽑아서 정리해 보았습니다 ~ 궁금하거나 더 추가되었으면 하는 문제가 있으면 페이스북 메시지 보내주세요 !


     



 