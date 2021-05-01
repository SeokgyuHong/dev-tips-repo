### control-plane 노드의 taint 지정을 해제하는 방법.md
--------------------
### 이유
클러스터 구축한 마스터 노드가 이상하게도 control-plane으로 지정된 상황이 있었다. control-plane인경우 taint(노드가 포드 셋을 제외할 수 있게 하는것)에 NoSchedule조건이 기본으로 걸려있다.

![image](https://user-images.githubusercontent.com/58390757/116782427-fd4da180-aac3-11eb-8fa2-2c8b6722ee11.png)

-----------------
### 해결방법
 `kubectl taint nodes <노드이름> node-role.kubernetes.io/master-`
 
 <img width="644" alt="스크린샷 2021-05-01 오후 9 30 51" src="https://user-images.githubusercontent.com/58390757/116782516-8238bb00-aac4-11eb-99e0-79a9e5a2e58d.png">
