## Understanding Kubernetes Objects(Resources)

### 1. Objects

* Kubernetes는 Object와 함께 동작한다.
* Object의 종류는 다음과 같다.
    * Pods
    * Deployments
    * Services
    * Volumes
    * others
* Object는 두 가지 방법으로 만들어진다.
    * imperatively 
    * declaratively

### 2. The Pod Object

* The smallest unit kubernetes interacts with
* Contains and runs one or multiple containers
* The most common use case is "one container per pod"
* Pods contain shared resources for all Pod containers
* Pod has a cluster internal IP by default
* Containers inside a Pod can communicate via localhost
* A Pod which has running containers is placed on some worker node
* Pods and designed to be ephemeral
    * Kubernetes will start, stop and replace them as needed
    * container 처럼 일시적으로 데이터를 저장하며 pod가 종료되면 데이터가 모두 삭제된다.
* Pods 관리를 위해 Controller(Deployment) Object 가 존재한다.