## Restarting Containers

### 1. 서비스 fail and restart

* /projects/2022-07-07-kub-action-01-starting-setup 프로젝트 참고
* /error 경로에 요청 시 서비스가 종료된다.
* 종료된 서비스를 Kubernetes가 Pods를 재실행하는지 확인한다.
* Kubernetes dashboard에서도 확인 가능하다.

```
$ curl http://192.168.59.100:30973/error
curl: (52) Empty reply from server

$ kubectl get pods
NAME                         READY   STATUS   RESTARTS        AGE
first-app-6c9d7ff88b-frh78   0/1     Error    3 (5m18s ago)   4h58m

$ kubectl get pods
NAME                         READY   STATUS             RESTARTS      AGE
first-app-6c9d7ff88b-frh78   0/1     CrashLoopBackOff   3 (20s ago)   4h58m

$ kubectl get pods
NAME                         READY   STATUS    RESTARTS      AGE
first-app-6c9d7ff88b-frh78   1/1     Running   4 (48s ago)   4h58m
```