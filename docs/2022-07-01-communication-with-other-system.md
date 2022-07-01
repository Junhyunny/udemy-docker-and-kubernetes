## Communication with other system

* `/projects/2022-07-01-networks-starting-setup` 프로젝트를 참고

### 1. Creating a container and communicating to the web

* 컨테이너 내부에서 외부 호출은 가능하다.
* 별도의 설정은 필요없다.

### 2. Making container to host communication work

* `localhost` 키워드를 `host.docker.internal`로 변경한다.
* `host.docker.internal`는 도커 엔진이 호스트 머신을 찾을 수 있는 스페셜 도메인이다.

### 3. Container to container communication: A basic solution

* 아래 명령어를 통해 mongo DB를 실행한다.

```
$ docker run -d --name mongodb mongo
```

* 아래 명령어를 통해 컨테이너 상세 정보를 확인한다.

```
$ docker container inspect mongodb
[
    {
        "Id": "9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94",
        "Created": "2022-07-01T08:23:20.581316067Z",
        "Path": "docker-entrypoint.sh",
        "Args": [
            "mongod"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 42969,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2022-07-01T08:23:20.839636711Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:c8b57c4bf7e3a88daf948d5d17bc7145db05771e928b3b3095ca4590719b5469",
        "ResolvConfPath": "/var/lib/docker/containers/9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94/hostname",
        "HostsPath": "/var/lib/docker/containers/9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94/hosts",
        "LogPath": "/var/lib/docker/containers/9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94/9276c6ea910d087eb1b1218bf7755116d1debcf8e39904d63994b816670ecb94-json.log",
        "Name": "/mongodb",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/230423ee6599ce823c5a08590a2337f3bcdb3bf1b8ab223eb4b1c32994de34e9-init/diff:/var/lib/docker/overlay2/05b8f47fbb06e2d1926d69bede0708d0885e21d9a222ac79f8beb5e671376a4a/diff:/var/lib/docker/overlay2/23e2f214e540f720a9cebb0ec5c898c232878de38dabee6d5e656a6dece13d02/diff:/var/lib/docker/overlay2/db2b649678400ec660e362e4a97d6b478bead8c8e976ec1d300a1fdd256d0310/diff:/var/lib/docker/overlay2/108374d89c7169b7d79394abb105d94d698d6037314f3e1f4ddbf25feb69dfb4/diff:/var/lib/docker/overlay2/1a552dcfd4fc843072ab2e1a65e5607817fe10a59c1dd6cefc28a88a9bb7907d/diff:/var/lib/docker/overlay2/f1c6d139602457cfe779c0d9c6cc2f4d17dd2350e0b772861ad505def63131bb/diff:/var/lib/docker/overlay2/593c5b943edc3726ea2975113a10c99e2e311197fdea9480310eac2bfac67d95/diff:/var/lib/docker/overlay2/f99ca7837236dc67ebf78ea23c6abff4a0e18e2f4e5e0ddb18392aa036c1f370/diff:/var/lib/docker/overlay2/37d1aebe0043a948b2446df36f99dd2f9aa2859c845a8bcd9fc72068b4b46087/diff",
                "MergedDir": "/var/lib/docker/overlay2/230423ee6599ce823c5a08590a2337f3bcdb3bf1b8ab223eb4b1c32994de34e9/merged",
                "UpperDir": "/var/lib/docker/overlay2/230423ee6599ce823c5a08590a2337f3bcdb3bf1b8ab223eb4b1c32994de34e9/diff",
                "WorkDir": "/var/lib/docker/overlay2/230423ee6599ce823c5a08590a2337f3bcdb3bf1b8ab223eb4b1c32994de34e9/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "volume",
                "Name": "1e7e311975dc11795a29386c0b27ae9926b7f6860e27236d7aeb7707d8ce3269",
                "Source": "/var/lib/docker/volumes/1e7e311975dc11795a29386c0b27ae9926b7f6860e27236d7aeb7707d8ce3269/_data",
                "Destination": "/data/configdb",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            },
            {
                "Type": "volume",
                "Name": "d9332d16d49fbfea549d11743aed07fdd49e7780ee31eb374d44780c817fc4d1",
                "Source": "/var/lib/docker/volumes/d9332d16d49fbfea549d11743aed07fdd49e7780ee31eb374d44780c817fc4d1/_data",
                "Destination": "/data/db",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
        "Config": {
            "Hostname": "9276c6ea910d",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "27017/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "GOSU_VERSION=1.12",
                "JSYAML_VERSION=3.13.1",
                "MONGO_PACKAGE=mongodb-org",
                "MONGO_REPO=repo.mongodb.org",
                "MONGO_MAJOR=5.0",
                "MONGO_VERSION=5.0.9",
                "HOME=/data/db"
            ],
            "Cmd": [
                "mongod"
            ],
            "Image": "mongo",
            "Volumes": {
                "/data/configdb": {},
                "/data/db": {}
            },
            "WorkingDir": "",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "723b6f4fafe01c82e1ed9bacb4b488205df0b7cd7b6cacfff61bf7b9e5b40ed3",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "27017/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/723b6f4fafe0",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "2f261579b60f72640e7a87a7e395431feabd74eba83e2307f15e38168dabcdad",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.3",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:03",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "41738f1822874f3b10e462e3f46d962d5a5717e7b2a74e2298a798e7064799ab",
                    "EndpointID": "2f261579b60f72640e7a87a7e395431feabd74eba83e2307f15e38168dabcdad",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.3",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:03",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

* 상세 정보에서 찾은 IP 주소로 접속한다.
    * 강의에서는 됬지만, 내 로컬 호스트에서는 실패