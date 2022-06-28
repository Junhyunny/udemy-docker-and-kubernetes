## Named volumes to the rescue

### 1. Two types of external data storages

* Volumes
    * Managed by docker
    * 두 종류의 볼륨이 존재
        * Anonymouse Volumes
        * Named Volumes
    * 두 종류의 볼륨 모두 호스트 머신에 어딘가에 존재
    * `docker volume` 명령어를 통해 관리
    * Docker에 의해 관리되므로 위치를 찾기 힘들지만, 찾을 수 있고 변경할 수 있다.
* Bind mounts
    * managed by developer

### 2. Anonymouse Volumes

* 컨테이너가 존재하는 동안만 존재한다.
* 컨테이너를 종료하고 삭제하면 함께 사라진다.

```
$ docker run -p 3000:80 -d --name feedback-app --rm feedback-node:volumes
8ab4c91a0a268657a0fb683f82097f20f1008209a760811ab8382e6da259b318

$ docker volume ls                                                       
DRIVER    VOLUME NAME
local     149d1273588ef6050f78312a54581f607b689c6cd96f35245e35b824b11655f4

$ docker stop feedback-app
feedback-app

$ docker volume ls        
DRIVER    VOLUME NAME
```

### 3. Named Volumes

* 컨테이너가 삭제되더라도 유지되는 볼륨
* 데이터를 유지하기 위해 사용
* `-v volume_name:directory_in_container` 옵션으로 볼륨을 지정

```
$ docker run -p 3000:80 -d --name feedback-app --rm -v feedback:/app/feedback feedback-node:volumes

$ docker volume ls
DRIVER    VOLUME NAME
local     feedback
```
