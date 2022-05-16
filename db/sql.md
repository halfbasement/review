# SQL


- Between ~ AND  ( where 범위 )
```sql
select * from member where height >= 163 and height <= 165;

비트윈으로 쉽게 사용 가능
-> select * from member where height between 163 and 165; 
```

- IN () (  or 축약 )
```sql
select * from member where name="홍길동" OR name="김첨지" OR name = "이순신";

-> 문자형 데이터

select * from member where name IN("홍길동","김첨지","이순신");
```

- LIKE 

```sql
select * from member where name LIKE "홍%" // 홍 뒤에 뭐든지 허용
select * from member where name LIKE "_순신" //앞 글자는 신경 X 뒤에는 순신 
```

- 서브쿼리 (  셀렉문 하나로 합치기 )

```sql

홍길동의 나이보다 높은 사람 찾기

1. select age from member where name = "홍길동"; // ex) ->20

2. select name,age from member where age >= 20;

------ 서브쿼리 사용 --------
select name,age from member where age>=( select age from member where name ="홍길동");



```

- Group by ( 그룹으로 묶어줌 ) // Having -> group by 조건
```sql
select sum(amount * price) as '합계' from buy group by mem_id;

member별로 구매한 가격
```

### MySQL 데이터형식

- unsigned : 0부터 시작함
- 숫자의 의미를 가지려면
    1. 더하기 / 빼기등의 연산에 의미가 있는 것
    2. 크다 / 작다 또는 순서에 의미가 있는 것

- BLOB : 글자가 아닌 이미지 , 동영상등의 데이터 ( 이진 데이터 )


### 조인

- 조인을 위해서는 일대다 관계로 연결되어야한다.

1. 내부조인 : 두 테이블에 모두 있는 내용만 조인
2. 외부조인 : 한쪽에만 데이터가 있어도 나옴
    - left ( outer ) join : 왼쪽테이블의 내용은 모두 출력되어야한다
3. 셀프조인 : 자신과 조인하면 됨