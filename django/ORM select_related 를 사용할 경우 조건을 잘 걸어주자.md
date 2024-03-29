###  ORM select_related 를 사용할 경우 조건을 잘 걸어주자
--------------

### 문제상황

건강검진 서비스 앱 개발을 진행하면서 ORM을 자주 사용하는 경우가 있었다. 학생들은 주기적으로 건강검진을 진행을 하기에 데이터베이스에 학생테이블과 건강검진 기록 테이블을 1:N관계로 설정해뒀다. 
또한 학생들이 졸업을 하는 경우에도 건강검진 기록 데이터를 유지해야 해서 졸업생테이블과 건강검진 기록테이블 역시 1:N관계로 설정해줬다.
서버가 학생 정보 삭제를 요청할 경우 -> 학생정보를 졸업생 테이블로 옮김 -> 해당학생 건강검진 기록들을 졸업생테이블과 매핑 -> 학생테이블 레코드 삭제( set null조건을 통해 건강검진 테이블 레코드와 관계를 끊는다)
의 흐름으로 구성했는데 웹 페이지 유저가 학생들의 건강검진 기록을 조회할때 문제가 생겼다.

-----------

장고에서 orm을 사용해 참조하는데 정참조의 경우 select_related를 사용해 참조할 수 있다. select_related를 사용할 경우 join쿼리로 변경해 쿼리가 나가고 결과물을 받아오는 구조다.
그런데 이 select_related를 활용한 join은 필터링 조건에 따라 inner join과 outer join이 달라진다. 

![image](https://user-images.githubusercontent.com/58390757/119596606-779ae880-be1a-11eb-96ea-30f3ec4a3d3a.png)

![image](https://user-images.githubusercontent.com/58390757/119596638-884b5e80-be1a-11eb-8a0f-d70e5c4531fc.png)

정참조 관계에서 해당객체가 참조하는 객체쪽에 조건을 걸어줘야 inner join으로 성립이된다. 필터조건을 잘못 건다면 졸업생들의 건강기록까지 한번에 조회하는경우가 생기기 때문에 조심하자..석규야

