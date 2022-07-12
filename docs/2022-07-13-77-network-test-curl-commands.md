## cURL command for Kubernetes network test

##### make users-service 

```
$ minikube service users-service    
|-----------|---------------|-------------|-----------------------------|
| NAMESPACE |     NAME      | TARGET PORT |             URL             |
|-----------|---------------|-------------|-----------------------------|
| default   | users-service |        8080 | http://192.168.59.100:32667 |
|-----------|---------------|-------------|-----------------------------|
🎉  Opening service default/users-service in default browser...
```

##### 로그인 정보 요청

```
$ curl -X POST http://192.168.59.100:32667/login\
   -H 'Content-Type: application/json'\
   -d '{"email":"test@test.com","password":"testers"}'
```