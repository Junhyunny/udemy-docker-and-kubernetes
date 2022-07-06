## Core Components

* Cluster
    * A set of Node machines which are running the Containerized application - Worker Nodes
    * Control other Nodes(Master Nodes)
* Nodes
    * Physical or virtual machines with a certain hardware capacity which hosts one or multiple Pods and communicates with the Cluster
    * Master Node - Cluster Control Plane, managing the Pods across Worker Nodes
    * Worker Node - Hosts Pods, running App Containers(+ resources)
* Pods
    * hold the actual running app containers
    * their requried resources(ex, volumes)
* Containers
    * Normal Docker Containers
* Servies
    * A logical set(group) of Pods with a unique
    * Pod and container independent IP address
    * Important to reaching our pods, therefor the containers inside of them
    * Service is related with proxy things
    * exposing certain pods to the outside world