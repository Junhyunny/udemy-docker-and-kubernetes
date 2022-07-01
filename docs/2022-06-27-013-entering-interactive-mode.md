## Entering interactive mode

### 1. docker run -i 옵션

* interactive 모드, 표준 입력(STDIN)을 활성화하여 컨테이너와 attached 모드가 아니더라도 표준 입력을 유지
* /projects/2022-06-27-python-app-starting-setup 참고

```
$ docker run -i 0cc94ec7a644
Please enter the min number: 123
Please enter the max number: 123
123
```

### 2. docker run -t 옵션

* `-t` 플래그는 TTY(pseudo-TTY)를 할당
* `bash`를 사용하기 위해선 이 옵션이 필요

```
$ docker run -it 0cc94ec7a644
Please enter the min number: 123
Please enter the max number: 123
123
```

### 3. docker start -i, -a 옵션

* `-i` 옵션 - 표준 입력을 활성화하여 표준 입력을 유지
* `-a` 옵션 - attached 모드 실행

```
$ docker ps -a                   
CONTAINER ID   IMAGE          COMMAND           CREATED         STATUS                          PORTS     NAMES
7ff973975623   0cc94ec7a644   "python rng.py"   3 minutes ago   Exited (0) About a minute ago             vibrant_dijkstra

$ docker start -a -i 7ff973975623 
Please enter the min number: 1  
Please enter the max number: 3 
3
```