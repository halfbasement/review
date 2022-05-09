# JDBC

##  JDBC 


애플리케이션 서버와 DB - 일반적인 사용법

1. 커넥션 연결 : 주로 TCP/IP를 사용해서 커넥션 연결
2. SQL 전달 : 애플리케이션 서버는 DB가 이해 할 수 있는 SQL을 연결된 커넥션을 통해 DB에 전달
3. 결과 응답 : DB는 전달된 SQL을 수행하고 그 결과를 응답

    - 이 방법은 DB마다 다 대응을 달리 해줘야하는데 이걸 파훼한게 **JDBC**다 ( 인터페이스 , 추상화에 의존 )
    - 인터페이스만 있다고 기능동작 x 회사에 맞는 jdbc드라이버 라이브러리를 다운 받아야함

1. Connection - 연결
2. Statment  - sql을 담은 내용
3. ResultSet - sql요청 응답




## JDBC를 편리하게 사용하는 기술

- jdbc를 직접 사용하는것은 상당히 불편하다



1.  SQL MAPPER( MYBATIS ,JdbcTemplate )
```
애플리케이션 로직 -> sqlMapper -> jdbc
```
2. ORM( JPA )

```
애플리케이션 로직 -> JPA <--JPA구현체 -> jdbc
```

**결국 이 기술들도 모두 JDBC를 사용하기 때문에 JDBC는 꼭 알아야한다**



##  DriverManager 커넥션 요청 흐름

1. DriverManager.getConnection()으로 커넥션 요청 

2. 맞는 드라이버 찾아서 커넥션반환 ( h2, mysql 등등)





