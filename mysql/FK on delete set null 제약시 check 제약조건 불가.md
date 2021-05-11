### FK on delete set null 제약시 check 제약조건 불가

---------------
### 문제상황

1개의 테이블에서 서로다른 table을 참조하는 2개의 fk에 대해 
`alter table <table> add contraint check (<column1> is not null or <column2> is not null);`

제약 조건을 걸었을때 Error number: 3823 에러가 발생했다.
mysql 홈페이지에서 에러 코드를 검색해보니

Error number: 3823; Symbol: ER_CHECK_CONSTRAINT_CLAUSE_USING_FK_REFER_ACTION_COLUMN; SQLSTATE: HY000

Message: Column '%s' cannot be used in a check constraint '%s': needed in a foreign key constraint '%s' referential action. 

fk 참조 제약조건을 수정하라는듯한 메시지가 나왔다.

----------
### 해결방법
2개의 fk에 대해 1개는 on delete set null;
1개는 on delete restrict; 
조건을 걸어놨었는데 추측하기론 set null 조건을 걸어버리면 강제로 null값으로 변해버리기 때문에 check조건에 성립한 값들이 성립하지 않는 오류가 발생 해버릴 수 있기 때문이라고 판단했다.

그래서 결론은 on delete set null; 조건을 지우면된다.
