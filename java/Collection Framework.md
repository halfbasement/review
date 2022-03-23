# Collection Framework

- 데이터 군을 저장하는 클래스들을 표준화한 설계
- 인터페이스
- Collection을 상속한 List , Set & Map (List&Set과는 다른 형태로 컬렉션을 다룸)

## List
- 순서가 있는 데이터 집합 / 중복 O
- 구현 클래스 : ArrayList , LinkedList , Vector 

1. ArrayList
    - object 배열을 이용해서 데이터 순차 저장
    - **배열에 공간이 없으면 보다 큰 배열 생성해서 복사**

2. LinkedList

    - 배열은 크기를 변경 할 수 없고 ( 복사해야함 ) , 비순차적인 데이터의 추가 또는 삭제에 시간이 많이 걸림
    - 이러한 단점을 극복하기위해 나옴 
    - 배열의 삭제가 매우쉬움 , 현재 요소의 이전 요소가 현재 요소의 다음 요소를 가르키게 하면 됨
    - 그러나 단방향이기 때문에 역방향 흐름의 접근이 어려움
    - 이 점을 보완한 것이 더블 링크드 리스트

- 결론 : 순차 추가삭제 ArrayList가 더 빠름 / 중간 추가삭제 LinkedList가 더 빠름


## Set
- 순서가 없는 데이터 집합 / 중복 X

## Map
- Key , Value 쌍 데이터 집합 / 키 중복 x 값 o
