## The Service Object(Resource)

### 1. Service Object

* Pod에 접근하기 위해 필요한 Objects
* Service Object has responsible for exposing pods to the cluster or externally
* Pod는 기본적으로 Internal IP가 존재하며 Pod가 교체될 때 같이 변경된다.
* Internal IP는 클러스터 외부에서 접근 불가능하다.
* Finding Pods is hard if the IP changes all the time
* Services group Pods with a shared IP address
* shared IP는 변경되지 않는다.
* Pod에 접근은 변경되지 않는 Service의 shared IP 주소를 통해 이뤄진다.
* Services can allow external access to Pods
* The default can be overwritten (internal only)
* Without Services, Pods are very hard to reach and communication is difficult because IP is changed
* 클러스터 외부에서 Pod에 접근하는 것은 서비스 없이는 불가능하다.