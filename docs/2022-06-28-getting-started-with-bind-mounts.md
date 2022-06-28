## Getting started with bind mounts

### 1. Bind Mount

* `bind mount` 할 때 지정하는 폴더, 경로는 개발자가 지정한다.
* 데이터를 유지하는 것과 변경하는 것이 모두 가능하다.
* `-v absolute_path_on_host:work_dir_container` 옵션으로 바인딩 지정
* 바인딩하면 경로가 모두 호스트의 경로로 매핑되기 때문에 호스트에 자원이 없는 경우 에러가 발생한다.

```
$ docker run -p 3000:80 -d --name feedback-app -v feedback:/app/feedback -v "/Users/junhyunk/Desktop/workspace/udemy/udemy-docker-and-kubernetes/projects/2022-06-28-data-volumes-03-adj-node-code":/app feedback-node:volumes
```

### 2. Docker file sharing

* Preference > Resources 설정
    * file sharing 에서 해당 경로를 추가해야 파일 공유가 가능