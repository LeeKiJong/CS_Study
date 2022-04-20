# Spring_Study
### [Spring의 등장 배경]
<p>EJB를 사용하면 애플리케이션 작성을 쉽게 할 수 있다. 이는 Tracnsaction 관리가 용이하고 로긴, 분산처리, 보안 등에 적합하지만, 개발의 효율성이 낮아지고 개발속도도 떨어지며 배우기 어렵고, 설정해야 할 부분이 많다. 그래서 그 대안으로 나온 게 Spring</p>  

---  

### [Spring Framework]
<p>경량화 된 솔루션. JEE가 제공하는 다양한 기능을 제공하는 것 뿐만 아니라, DI(Dependency Injection)나 AOP(Aspect Oriented Programming)와 같은 기능도 지원한다.
즉, 개발자가 복잡하고 실수하기 쉬운 Low Level에 신경 쓰지 않고 Business Logic 개발에 전념할 수 있도록 해준다.  
  
**AOP** </p>
```
1. 관심사의 분리를 통해서 소프트웨어의 모듈성을 향상한다.
2. 공통 모듈을 여러 코드에 쉽게 적용 가능하다.
```  

---  


### [Spring Framework Module]
**1. Spring Core**  
Spring Framework의 핵심 기능을 제공하고, Core 컨테이너의 주요 컴포넌트는 BeanFactory이다.    
  
**2. Spring Context**  
Spring을 컨테이너로 만든 것이 Spring core의 BeanFactory라면, Spring Framework로 만든 것은 Context module이다. 이 module은 국제화된 메시지 Application 생명주기 이벤트, 유효성 검증 등을 지원함으로써 BeanFactory의 개념을 확장한다.    
  
**3. Spring AOP**  
설정관리 기능을 통해 AOP기능을 Spring Framework와 직접 통합 시킨다.    
  
**4. Spring DAO**  
Spring JDBC DAO 추상 레이어는 다른 데이터베이스 벤더들의 예외 핸들링과 오류 메세지를 관리하는 중요한 예외계층을 제공한다.   
  
**5. Spring ORM(Web)**  
Spring Framework는 여러 ORM(Object Relational Mapping) Framework에 플러그인 되어, Object Relational(ex, JDO, Hibernate, iBatis)를 제공한다.    
  
**7. Spring Web MVC**  
Spring Framework는 자체적으로 MVC 프레임워크를 제공하고 있다. 스프링만 사용해도 MVC기반의 웹 어플리케이션을 어렵지 않게 개발 할 수 있다.    
  

---

### [IoC]
: Inversion of Control, 제어의 역행  
```
객체지향 언어에서 Object간의 연결 관계를 런타임에 결정  
객체 간의 관계가 느슨하게 연결됨(loose coupling)  
IoC의 구현 방법 중 하나가 DI
```
**Spring DI Container**
```
Spring DI Container가 관리하는 객체를 빈(Bean)이라 한다.  
빈들의 생명주기를 관리한다는 뜻으로 빈 팩토리라 한다.  
BeanFactory에 여러 가지 컨테이너 기능을 추가한 ApplicationContext가 있다.  
```
![image](https://user-images.githubusercontent.com/52438368/163546394-254bf92c-dc27-4187-89ef-7862d167f8b8.png)  
**객체 제어 방식**  
기존 : 필요한 위치에서 개발자가 필요한 객체 생성 로직 구현  
IoC : 객체 생성을 Container에게 위임하여 처리    
  
**IoC 사용에 따른 장점**  
객체 간의 결합도를 떨어뜨릴 수 있음.  
  
**객체간 결합도가 높으면?**  
해당 클래스가 유지보수 될 때 그 클래스와 결합된 다른 클래스도 같이 유지보수 되어야 할 가능성이 높음.    
  

---  

### [DI(Dependency Injection) --> 의존성 주입]
**객체 간의 결합을 느슨하게 하는 스프링의 핵심 기술이다.**  
- 제어의 역행이라는 의미로 사용
- 느슨한 결합의 주요강점 : 객체는 인터페이스에 의한 의존관계만을 알고 있으며, 이 의존관계는 구현 클래스에 대한 차이를 모르는 채 서로 다른 구현으로 대체가 가능하다.
---
### [스프링 설정 파일]
- BeanFactory인터페이스  

**bean요소의 설정**
- id : 식별자
- name : id에 대한 별칭
- class : Bean클래스 이름
- autowire : 자동 와이어 여부
- scope : 객체 생성을 어떻게 할지 여부
```java
<bean....score = "singleton"> //객체를 한번만 생성하고, 그 후부터는 이미 생성된 객체를 재활용
<bean....score = "prototype"> //객체를 매번 new instance로 생성해서 반환함
```
- factory-method : 속성값으로 static method를 지정해서 해당 method를 이용하여 빈을 생성하도록 설정

---
### [의존 관계를 관리하기 위한 방법]
1. Construction Injection : 생성자를 통해서 의존관계를 연결시키는 것을 말함
2. Setter Injection : 클래스 사이의 의존관계를 연결시키기 위해서 setter메소드를 이용하는 방법을 말함.
**ApplicationContext.xml**
1. constructor-agr 요소속성
   - index : constructor의 몇 번째의 인수에 값을 전달할 것인지 지정
   - type : constructor의 어느 데이터형의 인수에 값을 전달할 것인지 지정
   - ref : 자식요소 <ref bean="빈 이름"/> 대신에 사용할 수 있다.
   - value : 자식요소 <value>값</value> 대신에 사용할 수 있다.
2. property요소의 속성
   - ref : 자식요소 <ref bean="빈 이름"/> 대신에 사용할 수 있다.
   - value : 자식요소 <value>값</value> 대신에 사용할 수 있다.
### [Spring MVC]
<p>
@Component  
  - @Controller  
  - @Service(유효성 검사, 페이징 처리)  
  - @Repository(CRUD)</p>  
