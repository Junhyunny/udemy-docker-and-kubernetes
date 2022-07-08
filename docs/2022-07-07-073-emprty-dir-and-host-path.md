## emptyDir vs hostPath vs CSI volume type

### 1. emptyDir와 hostPath 차이점

* emptyDir volume type
    * 하나의 Pod에 개별적으로 할당된 volume
    * Pod 내부에 container가 종료되더라도 Pod가 죽지 않는 이상 데이터는 유지된다.
* hostPath type
    * 실제 로컬 머신에 저장한다.
    * workerNode가 여러 개 있는 경우에는 여전히 Node에 종속된다.
    * 다른 Node에 위치한 경우 이에 접근하지 못한다.
* CSI type
    * Container Storage Interface
    * Flexible volume type
    * network file system(NFS)와 유사하다.