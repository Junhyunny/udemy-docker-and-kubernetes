## Understanding the problem 

* /projects/2022-06-28-data-volumes-01-starting-setup 참조
* 현상 1
    * 컨테이너를 실행 후 포스트를 하나 작성한다.
    * 컨테이너를 종료, 삭제한다.
    * 컨테이너를 새로 실행시키면 이전에 작성한 포스트가 존재하지 않는다. (docker run)
* 현장 2 
    * 컨테이너를 실행 후 포스트를 하나 작성한다.
    * 컨테이너를 종료한다.
    * 컨테이너를 다시 실행시키면 이전에 작성한 포스트가 존재한다. (docker start)