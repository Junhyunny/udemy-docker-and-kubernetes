## What have a problem and why kubernetes?

### 1. 컨테이너로 해결되지 않는 문제

* 매뉴얼 식으로 컨테이너를 배포하는 일은 관리하기 어렵다.
* 보안과 설정에 대한 우려도 많다.
* 컨테이너들은 충돌나거나 종료되었을 때 다른 컨테이너로 대체되어야 한다.
* 트래픽을 균등하게 분산시킬 수 있어야 한다.
* 트래픽 급증 시 더 많은 인스턴스들이 필요할 수 있다.

### 2. 왜 쿠버네티스를 사용해야 하는가?

* 컨테이너 health check, 자동적인 재배포가 가능
* 자동 스케일링이 가능
* Load balancer 기능 가능
* AWS ECS를 사용해도 모두 가능하지만, 특정 솔루션에만 한정된다. 