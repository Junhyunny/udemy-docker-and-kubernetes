## The Deployment Object

### 1. What is Deployment Object?

* Pod Object를 직접 만드는 일은 보통 없다.
* Deployment 오브젝트를 이용해 Pods의 개수 등을 관리해준다.
* Controls multiple Pods
* Developer set a desired state, Kubernetes then changes the actual state
    * Define which Pods and containers to run and the number of instances
    * Pod들을 적절한 Worker Node에 위치시킨다. (CPU, Resource가 적절한 Worker Node)
* Deployment 객체들이 멈추거나 삭제되면 롤백된다.
* Deployment 객체들은 동적으로, 자동으로 스케일 된다.
    * metric을 사용한다.
    * incoming traffic / CPU utilization
* Developers can change the number of desired Pods as needed
