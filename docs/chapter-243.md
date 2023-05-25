
## Chapter243. Deployment Options & Steps

* What kuberntes will do
    * Create your objects(pods) and manage them
    * Monitor Pods and re-create them, scale Pods etc.
    * Kubernetes utilizes the provided resouces to apply your configuration / goals
* What you need to do
    * Create the cluster and the nods instances(Worker and Master Nodes)
    * Setup API servers, kubelet and other Kubernetes services / software on nodes
    * Create other (cloud) provider resources that might be needed
        * e.g. Load Balanacer, Filesystems

* Deployment Options
    * Custom Data Center를 통해 배포
        * install and configure everything on your own
        * machines and kubernetes software
    * Cloud Provider를 통해 배포
        * install and configure most things on your own
            * create and connect machines
            * install configure software
            * manully or using kops
        * Use a managed service
            * Define cluster architecture
            * Service like AWS EKS
