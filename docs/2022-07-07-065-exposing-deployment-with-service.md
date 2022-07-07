## Exposing a Deployment with a Service

### 1. expose 명령어

* `kubectl expose` 명령어로 deployment에게 서비스 객체 생성을 요청한다.
* `--port` - 노출하고 싶은 포트
* `--type` - 서비스 객체의 타입
    * ClusterIP - 서비스를 클러스터-내부 IP에 노출시킨다. 이 값을 선택하면 클러스터 내에서만 서비스에 도달할 수 있다. 이것은 ServiceTypes의 기본 값이다.
    * NodePort - 고정 포트 (NodePort)로 각 노드의 IP에 서비스를 노출시킨다. NodePort 서비스가 라우팅되는 ClusterIP 서비스가 자동으로 생성된다. <NodeIP>:<NodePort>를 요청하여, 클러스터 외부에서 NodePort 서비스에 접속할 수 있다.
    * LoadBalancer - 클라우드 공급자의 로드 밸런서를 사용하여 서비스를 외부에 노출시킨다. 외부 로드 밸런서가 라우팅되는 NodePort와 ClusterIP 서비스가 자동으로 생성된다.
    * ExternalName - 값과 함께 CNAME 레코드를 리턴하여, 서비스를 externalName 필드의 콘텐츠 (예:foo.bar.example.com)에 매핑한다. 어떤 종류의 프록시도 설정되어 있지 않다.

```
$ kubectl expose deployment first-app --port=8080 --type=LoadBalancer
service/first-app exposed

$ kubectl get services
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
first-app    LoadBalancer   10.101.72.170   <pending>     8080:30973/TCP   30s
kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          5h58m
```

### EXTERNAL-IP pending 처리

* EXTERNAL-IP는 Cloud Provider의 IP이지만, 현재 minikube와 가상 머신을 이용해 구현했기 때문에 별도로 존재하지 않는다.
* minikube 명령어를 통해 변경이 가능하다.
* LoadBalancer 기능을 제공하는 Cloud Provider에 Service Object를 배포했다면 pending 되지 않는다.

```
$ minikube service first-app
|-----------|-----------|-------------|-----------------------------|
| NAMESPACE |   NAME    | TARGET PORT |             URL             |
|-----------|-----------|-------------|-----------------------------|
| default   | first-app |        8080 | http://192.168.59.100:30973 |
|-----------|-----------|-------------|-----------------------------|
🎉  Opening service default/first-app in default browser...
```