## Kubernentes will NOT manage your Infrastructure

### 1. Kubernentes가 하는 일

* What Kubernentes Will Do
    * Once setup...
    * Create your objects(Pods) and manage them
    * Monitor Pods and recreate them, scale Pods
    * Kubernetes utilizes the provied(cloud) resources to apply your configuration / goals
* What you need to do / setup
    * Create the cluster and the node instances (woker + master nodes)
    * Setup API server, Kubelet and other kubernetes services / softwrae on nodes
    * Create other cloud provider resources, load balancer, file systems 