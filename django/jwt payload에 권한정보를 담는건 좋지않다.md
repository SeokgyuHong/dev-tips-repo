### jwt payload에 권한정보를 담는건 좋지않다
------------------------
오늘배운내용 ..
지금 진행 중인 프로젝트는 유저의 권한에 따라 접근할 수 있는 API를 다르게 설정 해야했다. 
인증 방식으로 jwt 방식을 채택 했고 api별 permission을 어떻게 처리해줄지 고민했다.
내 생각은 로그인시 jwt 토큰 payload에 유저레벨마다 다른 정보를 부여해주고 매 permission 검증마다 해당 payload값을 사용하려했다.

그리고 DB에 있는 user_level 컬럼을두고 permission 검증때마다 가져와 사용하는 방법도 고려했는데 
'매번 불필요한 쿼리 한개가 더 날아가는거 아닐까' 생각하고 전자를 선택했다.

오픈카톡방에 해당 구조를 여쭤봤는데 
'토근에 권한 정보를 저장하고 토큰 값 가지고 권한을 확인하면 권한이 바뀐 시나리오는 어떻게 대응할것인지, 기존토큰이 만료되는건가' 라는 질문에 대답하지못했다 ㅠ
oauth2.0을 찾아보라고 말씀하셨다 .. 열심히 봐야겠다


그래서 계정 접근 권한은 jwt access token + refresh token을 활용한 세션 슬라이딩과 유사한 방식으로 처리하고
각 api별 퍼미션은 db user_level을 비교해 처리 하기로 했다
