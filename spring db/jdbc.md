# JDBC

##  JDBC 


애플리케이션 서버와 DB - 일반적인 사용법

1. 커넥션 연결 : 주로 TCP/IP를 사용해서 커넥션 연결
2. SQL 전달 : 애플리케이션 서버는 DB가 이해 할 수 있는 SQL을 연결된 커넥션을 통해 DB에 전달
3. 결과 응답 : DB는 전달된 SQL을 수행하고 그 결과를 응답

    - 이 방법은 DB마다 다 대응을 달리 해줘야하는데 이걸 파훼한게 **JDBC**다 ( 인터페이스 , 추상화에 의존 )

- DriverManage 커넥션 요청 흐름

1. DriverManager.getConnection()으로 커넥션 요청 
2. 맞는 드라이버 찾아서 커넥션반환 ( h2, mysql 등등)




## JDBC를 편리하게 사용하는 기술

1.  SQL MAPPER( MYBATIS ,JdbcTemplate )

2. ORM( JPA )


## 커넥션 풀

### 미리 커넥션을 생성해두고 재사용


- DB 커넥션 획득 과정

1. 애플리케이션 로직은 DB드라이버로 커넥션 조회
2. DB드라이버는 DB와 TCP/OP커넥션을 연결 ( 네트워크 연결 동작 )
등등

- 이 과정은 시간이 오래 걸리기때문에 커넥션풀을 사용한다
- 보통 커넥션풀은 커넥션을 10개정도 생성해둔다 ( 설정 가능 )
- 대표적인 커넥션풀 : HikariCp ( 스프링부트 기본 ) / commons-dbcp2 / tomcat-jdbc pool

