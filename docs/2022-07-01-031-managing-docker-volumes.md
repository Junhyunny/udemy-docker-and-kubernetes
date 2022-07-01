## Managing docker volumes

### 1. Docker 볼륨 관련 명령어

```
$ docker volume --help

Usage:  docker volume COMMAND

Manage volumes

Commands:
  create      Create a volume
  inspect     Display detailed information on one or more volumes
  ls          List volumes
  prune       Remove all unused local volumes
  rm          Remove one or more volumes

Run 'docker volume COMMAND --help' for more information on a command.
```

### 2. Docker 볼륨 확인

* `docker volume ls` 명령어를 통해 볼륨 리스트를 확인할 수 있다.

```
$ docker volume ls    
DRIVER    VOLUME NAME
local     6f9b670f23ed60d2ba5f1557ece3e5eb459507c83c88d426c5d09a9d73be3fa3
local     42f0f55883de1edf43967bba4a5abb98bd43827430f22303c5c69495ac505bc8
local     400de9fca1c5383bf0a31fc7bd0d0d2a9dbcaab9a8118a6dc14ff5f9e575d178
local     185925b922ba41988f4c02d49a9d2fc473d7bb703cb2387644057153f81114e3
local     feedback
```

### 3. 도커 볼륨 관리

* `Bind Mount` 시킨 볼륨은 도커가 따로 관리하지 않는다.
* `Anonymous Volume`, `Named Volume` 같은 경우에는 도커가 관리한다.
* 필요한 볼륨이 없다면 도커가 컨테이너를 실행할 때 함께 볼륨을 만든다. 

### 4. 볼륨 생성 

* `docker create` 명령어를 통해 도커 볼륨을 생성할 수 있다.

```
$ docker volume create --help

Usage:  docker volume create [OPTIONS] [VOLUME]

Create a volume

Options:
  -d, --driver string   Specify volume driver name (default "local")
      --label list      Set metadata for a volume
  -o, --opt map         Set driver specific options (default map[])
```

```
$ docker volume create feedback-files

$ docker volume ls                   
DRIVER    VOLUME NAME
local     6f9b670f23ed60d2ba5f1557ece3e5eb459507c83c88d426c5d09a9d73be3fa3
local     42f0f55883de1edf43967bba4a5abb98bd43827430f22303c5c69495ac505bc8
local     400de9fca1c5383bf0a31fc7bd0d0d2a9dbcaab9a8118a6dc14ff5f9e575d178
local     185925b922ba41988f4c02d49a9d2fc473d7bb703cb2387644057153f81114e3
local     feedback
local     feedback-files
```

### 5. 도커 볼륨 상세 정보 보기

* 도커 볼륨의 상세 정보는 `docker volume inspect` 명령어를 통해 확인이 가능하다.
* `/var/lib/docker/volumes/feedback/_data`는 실제 로컬 파일 시스템에 있는 경로가 아니다.
    * 도커 시스템을 위한 가상 머신에 존재하는 경로이므로 찾기 힘들다. 

```
$ docker volume inspect --help 

Usage:  docker volume inspect [OPTIONS] VOLUME [VOLUME...]

Display detailed information on one or more volumes

Options:
  -f, --format string   Format the output using the given Go template

$ docker volume inspect feedback
[
    {
        "CreatedAt": "2022-06-28T08:47:02Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/feedback/_data",
        "Name": "feedback",
        "Options": null,
        "Scope": "local"
    }
]
```

### 6. 도커 볼륨 삭제하기

* `docker volume rm VOLUME_NAME` 명령어로 삭제 가능하다.
* 컨테이너가 볼륨을 사용 중이면 삭제가 불가능하므로 컨테이너를 먼저 종료해야 한다.
* 볼륨을 삭제하면 저장된 데이터들은 모두 삭제된다.

```
$ docker volume rm feedback-files
feedback-files

$ docker volume ls
DRIVER    VOLUME NAME
local     42f0f55883de1edf43967bba4a5abb98bd43827430f22303c5c69495ac505bc8
local     185925b922ba41988f4c02d49a9d2fc473d7bb703cb2387644057153f81114e3
local     feedback
```