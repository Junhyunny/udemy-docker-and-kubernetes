## Using COPY VS Bind Mounts

### 1. COPY 명령어를 사용하는 이유

* Bind Mounts 기능을 사용하면 COPY 명령어를 통해 당시 시점의 스냅샷 코드를 옮기지 않아도 정상 동작한다.
* Bind Mounts 기능은 개발할 때만 사용하고, 운영 환경에서 사용하지 않는다.