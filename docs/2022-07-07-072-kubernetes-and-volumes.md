## Kubernetes and Volumes - More than docker Volumes

### 1. Understanding State

* State is data created and used by your application which must not be lost
* User-generated data, user accounts, ...
    * Often stored in a database but could also be files
* Intermediate results derived by the app
    * Often stored in memory temporary database tables or files
* So we need volumes

### 2. Kubernetes and Volumes

* Kubernetes can mount Volumes into Containers
* Kubernetes support power volume concepts
* A broad variety of Volume types / drives are supported
* We run our application possibly on multiple node and different cloud, hosting providers.
* So kubernetes support different types of volumes
    * quite flexible
    * regarding where the data is actually stored
* 다음과 같은 Volume 저장소를 사용한다.
    * Local Volume (ex, on Nodes)
    * Cloud Provider specific Volumes
* Volume lifetime depends on the Pod lifetime
    * the volumes are parts of the pods, started and managed by kubernetes
    * Volumes survive container restart(and removal) because inside the pod not container.
    * Volumes are removed when pods are destoryed

### 3. Kubernetes Volumes and Docker Volumes

* Kubernetes Volumes
    * support many different drivers and types
    * Volumes are not necessarily persistent
    * Volumes survive container restarts and removals
* Docker Volumes
    * basically no drivers / type support
    * Volumes persist until manually cleared
    * Volumes survive container restarts and removals
    