# java Exception

- 상위 예외를 catch로 잡으면 하위 예외까지 다 잡힌다
- RuntimeException을 제외한 나머지 예외는 컴파일러가 체크한다


## 예외를 처리 못하고 계속 던질 떄

- 일반적인 자바main()은 오류 로그를 보여준다
- was는 에러페이지를 보여준다


## 예외 처리 방법

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
``

