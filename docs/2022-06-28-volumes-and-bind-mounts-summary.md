## Volumes and bind mounts:Summary

### 1. 명령어 요약

* `docker run -v /app/data` - anonymous volume
* `docker run -v data:/app/data` - named volume
* `docker run -v /path/to/code:/app/code` - bind mounts

### 2. 볼륨 별 비교

* Anonymous Volume
    * 컨테이너에게 직접 할당된 볼륨
    * `--rm` 옵션 없이 컨테이너를 삭제, 실행하는 경우 삭제되지 않는다.
    * `--rm` 옵션과 함께 실행된 컨테이너의 경우 삭제되면 함께 제거된다.
    * 컨테이너 사이에 공유 불가능
    * 재사용 불가능
* Named Volume
    * Dockerfile에 의해 만들 수 없다.
    * 컨테이너 실행 시 `-v name:directory_on_container` 옵션으로 생성한다.
    * 특정 컨테이너에 종속되지 않으며, 여러 컨테이너가 공유할 수 있다.
    * 컨테이너가 실행, 중지에 영향받지 않고 Docker CLI(command line interface)를 통해서 제거한다.
    * 같은 컨테이너가 재사용할 수 있다.
* Bind Mounts
    * 호스트 머신 어디에 데이터가 저장되는지 파악할 수 있다.
    * 특정 컨테이너에 종속되지 않으며, 여러 컨테이너가 사용할 수 있다.
    * 컨테이너가 실행, 중지에 영향받지 않으며 호스트 파일 시스템을 통해 삭제한다.