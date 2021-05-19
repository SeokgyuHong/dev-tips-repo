### nfs client를 사용할 경우 nfs-common 설치를 까먹지 말자,,.md
---------

### 문제상황

nfs를 pv로 사용하는 주키퍼를 쿠버네티스에 설치하려고 하는 와중 주키퍼 파드가 계속 펜딩 상태에 놓여있었다.

----------

### 원인

![image](https://user-images.githubusercontent.com/58390757/118838886-0383b080-b901-11eb-9c02-d0a870056de8.png)

kubectl describe pods <파드이름> 명령어로 확인해보니 nfs pv로 마운트가 안되고있었다.
output 로그를 확인해보고 구글링 해보니 nfs 클라이언트에 nfs-common설치를 안해줘서 생긴 문제였다.

------------
### 해결방법

nfs client로 사용하는 노드들마다 nfs-common을 설치해서 해결했다..
까먹지말자 ,,
![image](https://user-images.githubusercontent.com/58390757/118839620-9b819a00-b901-11eb-88b9-bdd11c62540f.png)
