## Docker Network Drivers

* 도커 네트워크는 다른 종류의 드라이버들을 제공한다.
* 기본 드라이버는 `bridge`
* `host` 드라이버
    * For standalone containers, isolation between container and host system is removed 
    * (i.e. they share localhost as a network)
* `overlay` 드라이버
    * Multiple Docker daemons (i.e. Docker running on different machines) are able to connect with each other. 
    * Only works in "Swarm" mode which is a dated / almost deprecated way of connecting multiple containers
* `macvlan` 드라이버
    * You can set a custom MAC address to a container 
    * this address can then be used for communication with that container
* `none`
    * All networking is disabled.
* `Third-party plugins`
    * You can install third-party plugins which then may add all kinds of behaviors and functionalities