## Labels and Selectors

### 1. -l 옵션

* -l 옵션을 사용하면 쉽게 특정 라벨을 가진 리소스들만 작업이 가능하다.

```
$ kubectl get pods -l app=second-app
NAME                                     READY   STATUS    RESTARTS   AGE
second-app-deployment-66448ddc6b-bt8t4   1/1     Running   0          12m
second-app-deployment-66448ddc6b-tglzv   1/1     Running   0          12m
second-app-deployment-66448ddc6b-v2jmf   1/1     Running   0          12m

$ kubectl delete pods -l app=second-app
pod "second-app-deployment-66448ddc6b-bt8t4" deleted
pod "second-app-deployment-66448ddc6b-tglzv" deleted
pod "second-app-deployment-66448ddc6b-v2jmf" deleted
```