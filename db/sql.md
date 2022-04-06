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