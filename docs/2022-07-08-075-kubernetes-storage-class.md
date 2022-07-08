## Stoage Class

* Administrators find grain control over how storage is manage and how volumes can be configured
* Minikube에서 이미 standard 이 host-path 타입으로 지정되어 있다.

```
$ kubectl apply -f host-pv.yml   
persistentvolume/host-pv created

$ kubectl apply -f host-pvc.yml
persistentvolumeclaim/host-pvc created

$ kubectl get pv               
NAME      CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM              STORAGECLASS   REASON   AGE
host-pv   1Gi        RWO            Retain           Bound    default/host-pvc   standard                7m46s

$ kubectl get pvc
NAME       STATUS   VOLUME    CAPACITY   ACCESS MODES   STORAGECLASS   AGE
host-pvc   Bound    host-pv   1Gi        RWO            standard       8m
```
