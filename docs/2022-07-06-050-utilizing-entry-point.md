## Utilizing ENTRYPOINT

### 1. CMD 명령어와 차이점

* CMD의 경우 `docker run` 실행 시 함께 전달한 명령어에 덮어 씌여진다.(over writen)
* ENTRYPOINT의 경우 `docker run` 실행 시 함께 전달한 명령어를 뒤에 붙힌다.