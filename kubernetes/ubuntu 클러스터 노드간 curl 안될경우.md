### ubuntu 클러스터 노드간 curl 안될경우
-------------------
### 문제상황 및 원인
클러스터 내 nginx 파드의 ip와 포트로 curl이 안날아가는 문제가 발생했었다. 
<img width="531" alt="스크린샷 2021-05-01 오후 9 33 57" src="https://user-images.githubusercontent.com/58390757/116782580-f4110480-aac4-11eb-82d5-24a201768703.png">

gcp instance 방화벽도 허용해줬는데 원인은 ubuntu 방화벽이 원인이였다.

--------------------
### 해결방법
`sudo ufw disable` <방화벽 비활성화 비추천>

`sudo ufw allow <port>` 특정 port 방화벽 허용 
