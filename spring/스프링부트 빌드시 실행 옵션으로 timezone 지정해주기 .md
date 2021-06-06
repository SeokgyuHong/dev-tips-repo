### 문제상황
--------
카프카 컨슈머가 브로커에서 데이터를 받아와 mysql에 저장한 뒤 해당 데이터를 스프링 was에서 rest api 응답으로 담아 보내야 했다.
워크벤치에서 확인해본 bidtime의 컬럼 값과 domain 클래스에서 localtime 속성으로 받아온 데이터간의 시간 차이가 생기는 문제가 발생했다.

![image](https://user-images.githubusercontent.com/58390757/120930198-48904b00-c727-11eb-8747-d95dec3ada56.png)
<img src="https://user-images.githubusercontent.com/58390757/120930205-4e862c00-c727-11eb-9bc4-5e2363555a70.png" width="300" height="300">



--------
### 해결방법

jar파일 생성 실행 옵션으로 -Duser.timezone=Asia/Seoul로 지정해 주면 jar파일 빌드시 spring default timezone이 서울시간으로 지정된다.

나는 쿠버네티스 배포를 위해 도커파일로 도커 이미지를 생성 해줘야 했기에 entrypoint에 해당 옵션을 추가해줬다.

![image](https://user-images.githubusercontent.com/58390757/120930422-221edf80-c728-11eb-8adf-9afcc47f3063.png)

