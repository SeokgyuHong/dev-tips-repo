### kubeadm init시 Cgroup Driver가 달라 발생하는 문제.md
--------------------------
### 문제 발생 상황
쿠버네티스 클러스터 구축을 위해 마스터 노드에서 init시 아래와 같은 에러 발생
![image](https://user-images.githubusercontent.com/58390757/116781401-92996780-aabd-11eb-9e28-dbd7642aae45.png)

-------------------------
### 원인
도커를 처음 설치하면 도커에서 사용하는 Cgroup Driver는 cgroupfs 드라이버를 사용한다.
- 도커엔진은 리눅스 운영체제 기반으로 돌아가는데 리눅스 커널이 제공해주는 cgroupfs 드라이버를 사용한다. 쿠버네티스에서 권장하는 cgroup driver는 systemd 이므로 클러스터 init이 안되는 에러가 발생했다.

-------------------------
### 해결방법 
