
### Public ip를 이용해 kubeadm init 및 join 하는 방법
---------------
#### 적용한 이유
- GCP에서 1개의 계정(VPC)에서 마스터, 워커노드를 구축한것이 아닌 3개의 계정에서 각 인스턴스 1개씩 구성을 했다. 서로 다른 VPC환경이기에 클러스터 구축을 위해서 Public IP를 활용해 접근할 수 밖에 없었음.

--------------
#### 방법
- Kubeadmin을 이용해 클러스터 구축 할 경우 master노드에서 
- kubeadm init --apiserver-advertise-address < 마스터 노드 IP > --pod-network-cidr =<포드에서 사용할 네트워크 대역> 명령어로 init을 진행한다. 
- public ip를 사용해서 구성하기 위해선 Control plane을 명시해줘서 Init을 진행 해줘야한다.
- `kubeadm init --contrl-plane-endpoint < public ip : port > --pod-network-cidr = <포드에서 사용할 네트워크 대역>`
