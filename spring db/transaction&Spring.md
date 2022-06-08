# 트랜잭션 문제 해결

- 서비스 계층은 특정 기술에 종속적이지 않게 최대한 순수 자바코드로 작성해야한다

- service부분의 SQLException은 jdbc에 종속적이기 때문에 가급적 repository에서 처리해야한다( jdbc구현기술이 서비스 계층에 누수 됨)


1. repository 기술 서비스 계층에 누수 
2. 예외 누수 
3. jdbc 반복 문제

- 스프링은 이 문제들을 해결 할 수 있는 다양한 방법을 제공한다


## 트랜잭션 동기화

- 스프링은 **트랜잭션 동기화 매니저**를 제공한다 ( 쓰레드로컬을 사용해서 커넥션을 동기화해줌) / 쓰레드로컬 : 안전하게 커넥션을 보관해줌

1. 서비스에서 transactionManager.getTransaction()을 호출해서 트랜잭션을 시작한다.
2. 트랜잭션 매니저는 내부에서 dataSource를 사용해서 커넥션을 생성해서 AutoCommit(false)로 트랜잭션 동기화 매니저에게 보관한다
3. 서비스는 비즈니스 로직을 실행하면서 repository의 메서드들을 사용한다 ( repository는 보관된 커넥션을 사용한다)


## 트랜잭션 템플릿

- 기본적으로 중복되는 commit(),.rollback()등을 한번에 관리해준다
```java
txTemplate.executeWithoutResult((status) -> {
            try {
                bizLogic(fromId, toId, money);
            } catch (SQLException e) {
                throw new IllegalStateException(e);
            }
        });
```

- 이래도 결국에 txTemplate.executeWithoutResult부분은 순수 비즈니스 로직이 아니다.


## 트랜잭션 AOP
 
- 트랜잭션 프록시를 하나 만들어줌