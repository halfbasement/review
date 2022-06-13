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