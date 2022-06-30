# Database
### [KEY]
#### [Candidate Key(후보키)]
- Tuple을 유일하게 식별하기 위해 사용하는 속성들의 부분 집합. (기본키로 사용할 수 있는 속성들)
- 아래 2가지 조건 만족
```
- 유일성 : Key로 하나의 Tuple을 유일하게 식별할 수 있음
- 최소성 : 꼭 필요한 속성으로만 구성
```
#### [Primary Key (기본키)]
- 후보키 중 선택한 Main Key
- 특징
```
- Null 값을 가질 수 없음
- 동일한 값이 중복될 수 없음
```
#### [Alternate Key (대체키)]
- 후보키 중 기본키를 제외한 나머지 키 = 보조키
#### [Super Key (슈퍼키)]
- 유일성은 만족하지만, 최소성은 만족하지 못하는 키
#### [Foreign Key (외래키)]
- 다른 릴레이션의 기본키를 그대로 참조하는 속성의 집합
---
### [Join]
- 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 방법
#### [Join 종류]
- INNER JOIN
- LEFT OUTER JOIN
- RIGHT OUTER JOIN
- FULL OUTER JOIN
- CROSS JOIN
- SELF JOIN
#### [INNER JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671097-591420e7-44ad-4dcb-bca2-785d89046273.png)
#### [LEFT OUTER JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671280-755029e8-f646-495c-af0a-28a66fcf709d.png)

#### [RIGHT OUTER JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671302-e1dad76c-9bd4-4edb-b16c-d7ce053fcc01.png)

#### [FULL OUTER JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671320-bd9627f0-8723-4f04-acd7-b9a4cb42056b.png)

#### [CROSS JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671360-2cc3a3ef-3c20-4f26-b35c-20eeca1ca008.png)

#### [SELF JOIN]
![image](https://user-images.githubusercontent.com/52438368/176671397-ef88eda1-3453-4be7-b6bf-8e01889d5ae4.png)
---
### [SQL Injection]
- 해커에 의해 조작된 SQL 쿼리문이 데이터베이스에 그대로 전달되어 비정상적 명령을 실행시키는 공격 기법
#### [인증 우회(공격 방법 1)]
- 보통 로그인을 할 때, 아이디와 비밀번호를 input 창에 입력하게 된다. 쉽게 이해하기 위해 가벼운 예를 들어보자. 아이디가 abc, 비밀번호가 만약 1234일 때 쿼리는 아래와 같은 방식으로 전송될 것이다.
```sql
SELECT * FROM USER WHERE ID = "abc" AND PASSWORD = "1234";
```
- SQL Injection으로 공격할 때, input 창에 비밀번호를 입력함과 동시에 다른 쿼리문을 함께 입력하는 것이다.
```sql
1234; DELETE * USER FROM ID = "1";
```
- 보안이 완벽하지 않은 경우, 이처럼 비밀번호가 아이디와 일치해서 True가 되고 뒤에 작성한 DELETE 문도 데이터베이스에 영향을 줄 수도 있게 되는 치명적인 상황이다.  
- 이 밖에도 기본 쿼리문의 WHERE 절에 OR문을 추가하여 '1' = '1'과 같은 true문을 작성하여 무조건 적용되도록 수정한 뒤 DB를 마음대로 조작할 수도 있다.

#### [데이터 노출(공격 방법 2)]
- 시스템에서 발생하는 에러 메시지를 이용해 공격하는 방법이다. 보통 에러는 개발자가 버그를 수정하는 면에서 도움을 받을 수 있는 존재다. 해커들은 이를 역이용해 악의적인 구문을 삽입하여 에러를 유발시킨다.  

- 즉 예를 들면, 해커는 GET 방식으로 동작하는 URL 쿼리 스트링을 추가하여 에러를 발생시킨다. 이에 해당하는 오류가 발생하면, 이를 통해 해당 웹앱의 데이터베이스 구조를 유추할 수 있고 해킹에 활용한다.

#### [input 값을 받을 때, 특수문자 여부 검사하기(방어 방법 1)]
- 로그인 전, 검증 로직을 추가하여 미리 설정한 특수문자들이 들어왔을 때 요청을 막아낸다. 

#### [SQL 서버 오류 발생 시, 해당하는 에러 메시지 감추기(방어 방법 2)]
- view를 활용하여 원본 데이터베이스 테이블에는 접근 권한을 높인다. 일반 사용자는 view로만 접근하여 에러를 볼 수 없도록 만든다.  

#### [preparestatement 사용하기(방어 방법 3)]
- preparestatement를 사용하면, 특수문자를 자동으로 escaping 해준다. (statement와는 다르게 쿼리문에서 전달인자 값을 ?로 받는 것) 이를 활용해 서버 측에서 필터링 과정을 통해서 공격을 방어한다.

[출처] https://gyoogle.dev/blog/computer-science/data-base/SQL%20Injection.html
