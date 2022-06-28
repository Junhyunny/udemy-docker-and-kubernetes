## A NodeJS-specific adjustment: Using Nodemon in a container

### 1. JavaScript 코드 변경 시 미반영 현상

* `Bind Mount`로 프로젝트 저장소를 공유하더라도 JavaScript 코드 변경 사항은 확인하지 못한다.
* JavaScript 코드는 `NodeJS` 런타임에 의해 실행되기 때문에 컨테이너를 재실행하지 않으면 반영되지 않는다.