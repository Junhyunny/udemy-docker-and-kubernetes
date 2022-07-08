## Normal volumes vs Persistent Volumes

* Volumes allow you to persist data
* Normal Volumes
    * Container가 데이터를 잃어버리지 않도록 한다.
    * Volume is attached to Pod and Pod lifecycle
    * volume type 마다 다르다.
    * Defined and created together with Pod
    * Repetitive and hard to administer on a global level
        * Pod를 만들 때마다 필요한 Volume 설정이 반복적으로 필요하다.
* Persistent Volumes
    * Container가 데이터를 잃어버리지 않도록 한다.
    * Volume is a standalone Cluster (resource NOT attached to a pod)
    * Create standalone, claimed via a PVC
    * Can be defined once and used multiple times
    * 큰 프로젝트에서는 스토리지 관리를 더 쉽게 할 수 있다.