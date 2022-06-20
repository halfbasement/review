# java Exception

- 상위 예외를 catch로 잡으면 하위 예외까지 다 잡힌다
- RuntimeException을 제외한 나머지 예외는 컴파일러가 체크한다


## 예외를 처리 못하고 계속 던질 떄

- 일반적인 자바main()은 오류 로그를 보여준다
- was는 에러페이지를 보여준다


## 예외 처리 방법

### 체크 예외

```java
 /**
     * Checked 예외는
     * 예외를 잡아서 처리하거나 , 던지거나 둘 중 하나를 선택
     */
    static class Service{
        Repository repository = new Repository();

        /**
         * 예외를      잡아서 처리하는 코드
         */
        public void callCatch(){
            try {
                repository.call();
            } catch (MyCheckedException e) {
                log.info("예외 처리 , message={}",e.getMessage(),e);
            }
        }

        /**
         *
         * 예외를 안잡고      예외 던지기
         * @throws MyCheckedException
         */
        public void callThrow() throws MyCheckedException {
            repository.call();
        }
    }
```
- 체크예외 장단점 
1. 장점 : 컴파일 시점에 잡히기 때문에 누락 할 수가 없음. 
2. 단점 : 모든 체크 예외를 잡거나 던져야 하기 때문에 결국 처리하는 부분을 무조건 작성해야 하므로 번거롭다.




### 언체크 예외

- RuntimeException과 그 하위 예외는 언체크 예외다
- 예외를 잡아서 처리하지 않아도 throws를 생략 가능 ( 체크 예외는 생략 불가능 하다 )

- 언체크예외 장단점
1. 장점 : 언체크예외 무시가능
2. 단점 : 예외를 누락 할 수 있음 



## 기본 원칙

- 기본적으로 런타임(언체크)예외를 사용하자
- 체크예외는 비즈니스 로직상 의도적으로 던지느 예외에만 사용 ( 컴파일 시점에 알아 차리게 )
ex
1. 계좌 이체 실패 예외
2. 결제시 포인트 부족
3. 로그인 ID,PW 불일치 예외

### 그럼 체크 예외를 왜 안쓸까?

1. 서비스 계층 ( 자바코드 )의 로직에서 처리 할 수 없는 예외가 터질 수 있다 ( ex SQLException, ConnenctException) 

2. 그럼 method() throw Exception으로 컨트롤러에게 넘기는데 컨트롤러도 처리할 방법이 없다.

3. 불필요한 의존관계 - 무엇보다 SQLException같은예외를 넘겨버리면 **exception기술에 종속적이게 된다 ( 교체하기가 힘들어진다 )** 


## 정리

- 체크예외는 다루기 힘들기 때문에 스프링이나 기타 라이브러리들도 런타임(언체크)예외를 기본으로 사용한다 ( jpa, 스프링 등)
- 런타임예외를 기본으로 쓰고 필요시에 공통처리 부분을 만들면 된다
- 런타임 예외는 놓칠 수 있기 때문에 문서화가 필요하다



## 예외 포함과 스택트레이스 - 실무에서 중요함

- 예외를 전환 할때는 기존 예외를 포함해야한다 ( Throwable cause )


## 체크예외 -> 런타임 예외 변환

- 체크 예외를 런타임 예외로 변환하면 인터페이스와 서비스 계층의 순수성을 유지할 수 있다.
