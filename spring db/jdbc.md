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

-  SQL MAPPER( MYBATIS ,JdbcTemplate )

2. ORM( JPA )
