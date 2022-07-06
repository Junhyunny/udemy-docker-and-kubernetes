## A Closer Look at the Master Node

### 1. Master Node

* API Server
    * API for the kubelets to communicate, counter part
* Scheduler
    * Watche for new Pods
    * Selects Worker nodes to run them on
    * Create new pod when pods went down, unhealthy or scaling
* Kube-Controller Manager
    * Watches and controls Worker Nodes
    * Correct number of Pods
* Cloud Controller Manager
    * Like Kube-Controller Manager for a specific Cloud Provider(AWS, Azure)
    * Knows how to interact with Cloud Provider Resources