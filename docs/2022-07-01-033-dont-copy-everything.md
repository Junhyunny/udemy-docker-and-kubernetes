## Don't COPY everything: Using "dockerignore" files

### 1. .dockerignore 파일

* COPY 제외 대상을 지정할 수 있는 파일
* 해당 파일에 추가한 대상 폴더나 파일은 COPY 명령시 제외할 수 있다.
* 주요 제거 대상은 다음과 같다.
    * node_modules
    * target 
    * .git 