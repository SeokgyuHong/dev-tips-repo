
### 레거시 디비에서 model 가지고 오는 방법
-----------------
model.py 파일을 생성하고 migration을 통해 데이터베이스 스키마를 생성하는방법이 아닌
기존에 존재하는 데이터베이스를 model.py파일로 가지고 오는 방법

ERD cloud로 테이블 생성-> SQL 내보내기 및 쿼리 실행 -> model.py로 가져오기

`python3 manage.py inspectdb`

`python3 manage.py inspectdb > model.py` 
model.py파일로 바로 만들어준다.
