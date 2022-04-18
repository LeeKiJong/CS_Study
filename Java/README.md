# Java
### [OOP]
- OOP란 현실 세계를 프로그래밍으로 옮겨와 현실 세계의 사물들을 객체로 보고, 그 객체로부터 개발하고자 하는 특징과 기능을 뽑아와 프로그래밍하는 기법.
- 장점 : 재사용성과 변형가능성을 높일 수 있다.
**OOP의 5가지 설계 원칙**
```
- SRP(Single Responsibility Principle, 단일 책임 원칙): 클래스는 단 하나의 목적을 가져야 하며, 클래스를 변경하는 이유는 단 하나의 이유여야 한다.
- OCP(Open-Closed Principle, 개방 폐쇠 원칙): 클래스는 확장에는 열려 있고, 변경에는 닫혀 있어야 한다.
- LSP(Liskov Substitution Principle, 리스코프 치환 원칙): 상위 타입의 객체를 하위 타입으로 바꾸어도 프로그램은 일관되게 동작해야 한다.
- ISP(Interface Segregation Principle, 인터페이스 분리 원칙): 클라이언트는 이용하지 않는 메소드에 의존하지 않도록 인터페이스를 분리해야 한다.
- DIP(Dependency Inversion Principle, 의존 역전 법칙): 클라이언트는 추상화(인터페이스)에 의존해야 하며, 구체화(구현된 클래스)에 의존해선 안된다.
```
---
### [절차지향 프로그래밍 VS 객체지향 프로그래밍]
**절차지향 프로그래밍**
```
1. 순차적인 처리를 중요시하는 프로그래밍 기법.
2. 가장 대표적인 언어로 C언어
3. 컴퓨터의 처리구조와 유사해 실행속도가 빠르다.
4. 코드의 순서가 바귀면 동일한 결과를 보장하기 어렵다.
```
**객체지향 프로그래밍**
```
1. 실제 세계의 사물들을 객체로 모델링하여 개발을 진행하는 프로그래밍 기법.
2. 가장 대표적인 언어로 Java
3. 캡슐화, 상속, 다형성 등과 같은 기법을 이용
4. 실행속도는 절차지향보다 느리다.
```
---
### [RESTful API]
- REST(REpresentational State Transfer)ful API는 HTTP 통신에서 어떤 차원에 대한 CRUD 요청을 Resource와 Method로 표현하여 특정한 형태로 전달하는 방식
- Resource(자원, URI), Method(요청 방식, GET or POST), Respresentation of Resource(자원의 형태, JSON or XML) 로 구성
---
### [TDD(Test-Driven Development)]
- 매우 짧은 개발 사이클의 반복에 의존하는 개발 프로세스
- 우선 요구되는 기능에 대한 테스트케이스와 코드를 작성하고 상황에 맞게 리팩토링하는 테스트 주도 개발 방식.
---
### [DDD(Domain-Driven Design)]
- 실세계에서 사건이 발생하는 집합인 Domain을 중심으로 설계하는 방법.
- 도메인(손님, 점주 등)들이 서로 상호작용하며 설계. MSA를 적용하여 용이한 설계
---
### [MSA(Microservice Architecture)]
