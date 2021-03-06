# Programming_Study
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
- 우선 요구되는 기능에 대한 테스트케이스와 코드를 작성하고 상황에 맞게 리팩토링하는 **테스트 주도 개발 방식**.
---
### [DDD(Domain-Driven Design)]
- 실세계에서 사건이 발생하는 집합인 **Domain**을 중심으로 설계하는 방법.
- 도메인(손님, 점주 등)들이 서로 상호작용하며 설계. **MSA**를 적용하여 용이한 설계
---
### [MSA(Microservice Architecture)]
- 모든 시스템의 구성요소가 한 프로젝트에 통합되어 있는 모놀리식 아키텍처의 한계점을 극복하고자 등장.
- 1개의 시스템을 **독립적으로** 배포가능한 각각의 서비스로 분할.  
  
**장점**
```
1. 일부 서비스에 장애가 발생하여도 전체 서비스에 장애가 발생하지 않는다
2. 각각의 서비스들은 서로 다른 언어와 프레임워크로 구성될 수 있다.
3. 서비스의 확장이 용이하다.
```
**단점**
```
1. 서비스가 분리되어 있어, 테스팅이나 트랜잭션 처리 등이 어렵다.
2. 서비스 간에 RESTful API로 통신하기 때문에 그에 대한 비용 발생.
3. 서비스간의 호출이 연속적이기 때문에 디버깅이 어렵다.
```
---
### [함수형 프로그래밍]
- **immutable data, first class citizen**으로서의 함수
- 부수효과가 없는 순수 함수를 이용하여 프로그램 구성
---
### [메모리 구조]
![image](https://user-images.githubusercontent.com/52438368/163808614-6f00d971-2707-4ade-8b5a-8f80d127f986.png)  
- 코드 영역 : 실행한 프로그램의 코드가 저장되는 영역
- 데이터 영역 : 프로그램의 전역 변수(global)와 정적 변수(static)가 저장되는 영역
- 힙 영역 : 프로그래머가 직접 관리할 수 있는 메모리 영역. 이 공간에 메모리를 할당하는 것을 **동적 할당**이라고 한다. Java에서는 가비지 컬렉터가 자동으로 해제
- 스택 영역 : 함수의 호출과 함께 할당되며 지연 변수와 매개 변수가 저장되는 영역.
---
### [Parameter와 Argument의 차이]
- Parameter : 함수를 선언할 때 사용된 변수
- Argument : 함수가 호출되었을 때 함수의 파라미터로 전달된 실제 값
---
### [Call By Value와 Call By Reference 차이]
**Call By Value**
```
- 인자로 받은 값을 복사하여 처리하는 방식
- Call By Value에 의해 넘어온 값을 증가시켜도 원래의 값 보존
- 값을 복사하여 넘기기 때문에 메모리 사용량 증가
```
**Call By Reference**
```
- 인자로 받은 값의 주소를 참조하여 직접 값에 영향을 주는 방식
- 값을 복사하지 않고 직접 참조하기 때문에 속도가 빠르다.
- 원래의 값에 영향을 주는 리스크 존재
```
---
### [프레임워크와 라이브러리 차이]
**프레임워크** : 전체적인 흐름을 자체적으로 제어한다.  

**라이브러리** : 사용자가 흐름에 대한 제어를 하며 필요한 상황에 가져다가 쓸 수 있다.
```
- 프레임워크를 사용하면 사용자가 관리해야 하는 부분을 프레임워크에 넘김으로써 신경써야 할 것을 줄이는 제어의 역젼(Ioc, Inversion Of Control)이 적용
```
---
### [병렬 처리 프레임워크의 종류와 특징]
**Hadoop**
```
- HDFS(Hadoop Distributed File System)를 활용해 데이터를 주고 받는다.
- 데이터가 여러 노드에 분산되어 저장되기 때문에 손실의 우려가 없다는 장점
- 하지만 File I/O를 기반으로 작동하기 때문에 처리 속도가 느리다.
```
**Spark**
```
- In-Memory 상에서 데이터를 주고받고 연산을 수행한다.
- 메모리를 사용해 데이터를 처리하기 때문에 속도가 빠름
- 하지만 메모리상에서 처리하기 때문에 장애가 발생한 경우 응용 프로그램을 처음부터 다시 시작해야 한다.
```
---
### [동기와 비동기의 차이]
**동기**
```
- 요청을 보내고 실행이 끝나면 다음 동작을 처리, 제어가 쉽다.
- 여러가지 요청을 동시에 할 수 없어서 효율이 떨어진다. ex) 콜센터의 종업원
```
**비동기**
```
- 요청을 보내고 해당 동작의 처리 여부와 상관없이 다음 요청이 동작하는 방식
- 작업이 완료되는 시간을 기다릴 필요가 없기 때문에 자원을 효율적으로 사용할 수 있다.
- 제어가 어렵다, ex) 이메일
```
---
### [SQL Injection]
- 공격자가 악의적인 의도를 갖는 구문을 삽입하여 공격자가 원하는 SQL을 실행하도록 하는 웹해킹기법
