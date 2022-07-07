## Scaling in action

### 1. 스케일링 시키기

```
$ kubectl scale deployment/first-app --replicas=3
deployment.apps/first-app scaled

$ kubectl get pods
NAME                         READY   STATUS    RESTARTS        AGE
first-app-6c9d7ff88b-frh78   1/1     Running   4 (8m53s ago)   5h6m
first-app-6c9d7ff88b-wdtks   1/1     Running   0               12s
first-app-6c9d7ff88b-wk8qw   1/1     Running   0               12s
```

### 2. Load Balancing

```
$ curl http://192.168.59.100:30973/error
curl: (52) Empty reply from server

$ kubectl get pods
NAME                         READY   STATUS    RESTARTS        AGE
first-app-6c9d7ff88b-frh78   0/1     Error     4 (9m47s ago)   5h7m
first-app-6c9d7ff88b-wdtks   1/1     Running   0               66s
first-app-6c9d7ff88b-wk8qw   1/1     Running   0               66s
```