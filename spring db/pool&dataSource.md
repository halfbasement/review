# Connenction Pool & DataSource

## 커넥션 풀

### 미리 커넥션을 생성해두고 재사용


- DB 커넥션 획득 과정

1. 애플리케이션 로직은 DB드라이버로 커넥션 조회
2. DB드라이버는 DB와 TCP/OP커넥션을 연결 ( 네트워크 연결 동작 )
등등

- 이 과정은 시간이 오래 걸리기때문에 커넥션풀을 사용한다
- 보통 커넥션풀은 커넥션을 10개정도 생성해둔다 ( 설정 가능 )
- 대표적인 커넥션풀 : HikariCp ( 스프링부트 기본 ) / commons-dbcp2 / tomcat-jdbc pool
- db에 무한정 연결이 생성되는 것도 막아준다


## DataSource( 커넥션 획득방법을 추상화 하는 인터페이스 )

- 커넥션을 얻는 방법은 여러가지가 있다 ( driverManager나 커넥션풀 등)
- driverManager로 커넥션을 획득하다가 커넥션 풀로 변경시 애플리케이션 코드 변경이 필요함
- 자바에서는 이런 문제를 해결하기위해 javax.sql.datasource인터페이스 제공
- 커넥션을 획등하는 방법을 추상화 하는 인터페이스이다
- driverManager는 datasource인터페이스를 사용 x -> 스프링이 DriverManagerDataSource라는 DataSource를 구현한 클래스를 제공한다


- **DriverManager는 커넥션을 사용 할 때마다 설정 정보를 전달해야하지만 DataSource는 설정객체만 만들어서 단순히 호출만 한다(dataSource에만 의존하면 됨)**
- **설정과 사용의 분리**


### HikariConfig ( 커넥션풀 )
- 기본적으로 잔여커넥션이 없으면 대기한다
- 커넥션이 넘치면 풀이 회복될 때 까지 블락이 됨 ( 멈춰서 기다리다가 예외를 터뜨림)
- 커넥션풀을 사용하면 커넥션을 사용하고 다시 돌려준다 ( 재사용 )
- **DriverManagerDataSource HikariDataSource 로 변경해도 MemberRepositoryV1 의 코드는 전혀
변경하지 않아도 된다. MemberRepositoryV1 는 DataSource 인터페이스에만 의존하기 때문이다.
이것이 DataSource 를 사용하는 장점이다.(DI + OCP)**



### 정리

