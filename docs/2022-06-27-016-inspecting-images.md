## A look behind the scenes: Inspecting images

### 1. docker image inspect 명령어

* 특정 이미지에 대한 정보를 확인할 수 있다.
    * 고유 ID
    * 설정, Configuration
    * 환경 설정, ENV
    * 이미지 레이어 리스트

```
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
<none>       <none>    701a360a8f3c   16 minutes ago   1GB

$ docker image inspect 701a360a8f3c
[
    {
        "Id": "sha256:701a360a8f3c8230239306fc58d4c0916673abc13eb27f79c146b7d9bd751123",
        "RepoTags": [],
        "RepoDigests": [],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2022-06-26T17:31:46.747842379Z",
        "Container": "",
        "ContainerConfig": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": null,
            "Cmd": null,
            "Image": "",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null
        },
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NODE_VERSION=18.4.0",
                "YARN_VERSION=1.22.19"
            ],
            "Cmd": [
                "node",
                "server.js"
            ],
            "ArgsEscaped": true,
            "Image": "",
            "Volumes": null,
            "WorkingDir": "/app",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 1004219707,
        "VirtualSize": 1004219707,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/uoaei3ag70zyf2pci8hxzr0hc/diff:/var/lib/docker/overlay2/ydpp4kcp6yzjss5mkqsdn6p2o/diff:/var/lib/docker/overlay2/fef5a3d13fe73b0b4f0f70abd1df88f0beb7b8c80f3d119f00b616177c36954a/diff:/var/lib/docker/overlay2/1bb561491c376e463e35682ea3000105892908104ec0f2e26c22ccc2ee33cbea/diff:/var/lib/docker/overlay2/5799210bd37e1731d9ce0ca08d1d96a09e6174add119dda0361e20aec4cbc054/diff:/var/lib/docker/overlay2/4026f26703682a1b2f776ac567a30c7e52cc9aeebfd47af46ac9868270537536/diff:/var/lib/docker/overlay2/7a1546b0130925a63011315a7b99024562dc6f1454b1c52739707488168a48dc/diff:/var/lib/docker/overlay2/c6a3cf936b5c36d79df239b074799ee80c315d9a4dfbea155b5f18d0e1f87e34/diff:/var/lib/docker/overlay2/292f0473266a5075ba0e5f5999248a71e34c5a4447f1b41c0d4ea514b8ac42a7/diff:/var/lib/docker/overlay2/bc3a0a3b8f9cd5a3bc7f9fca364bbf2f153a59880bd1a86df7ee7b09c0fdda4a/diff:/var/lib/docker/overlay2/eac3d71afcd966fc86fe26dfe5b82f60e474ede8cae13be42ce6ef6952b275dd/diff",
                "MergedDir": "/var/lib/docker/overlay2/u3y222sogay6rk8jj1gc8r2me/merged",
                "UpperDir": "/var/lib/docker/overlay2/u3y222sogay6rk8jj1gc8r2me/diff",
                "WorkDir": "/var/lib/docker/overlay2/u3y222sogay6rk8jj1gc8r2me/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:97d5fec864d84417c057008f153140193d2cc924b545b0c6fec10ae891fb26f9",
                "sha256:6840c8ff46bd2c0ab4086d311c3e4903639b586c84d4f4ad28d156a2cc749e5f",
                "sha256:66183893ba248fa10375cfec3e598d7df626b44c7740156e935ce2fcd5589aa7",
                "sha256:5afd661c6106dfe99ed40c2dd18b8f6ffc5d978fa3302037b513c7a6e366609f",
                "sha256:33a247b4fc529be9d43b5e70cc7d1beadf12e58c6e74967a4ade33e5e58f936d",
                "sha256:231df8129a1a985fbf6c60bbef7f409e6610b1cfe742991d9bc86c8d1fcf538f",
                "sha256:b185bf98c447b5a294facb075bff4a78f61b1d2b64ad76f51062240fb6f049b2",
                "sha256:f4a4053d0f5bb1257749702c90307162f8eb519e369d26268b2890c21dbe6dcb",
                "sha256:28d8a5aca1e59a1b5c96fdc19ecec41319caac1cb26532717ddd477fc1b05db5",
                "sha256:ec7975e5866415635e2f126b6fb0746e934e01fc92bcfa19e18c019ff094841c",
                "sha256:bad7d4678efb6b4ba436580f90c4d01ead469074daefc1b2ea1ab153d7b3ef20",
                "sha256:80cb3f21adaed781526c33a7d381483b9d93f39b70315bb0001090a8fb05f26c"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]
```