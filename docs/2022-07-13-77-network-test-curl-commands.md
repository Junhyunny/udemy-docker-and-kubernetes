## cURL command for Kubernetes network test

##### make users-service 

```
$ minikube service users-service    
|-----------|---------------|-------------|-----------------------------|
| NAMESPACE |     NAME      | TARGET PORT |             URL             |
|-----------|---------------|-------------|-----------------------------|
| default   | users-service |        8080 | http://192.168.59.100:32667 |
|-----------|---------------|-------------|-----------------------------|
π  Opening service default/users-service in default browser...
```

##### λ‘κ·ΈμΈ μ λ³΄ μμ²­

```
$ curl -X POST http://192.168.59.100:32667/login\
   -H 'Content-Type: application/json'\
   -d '{"email":"test@test.com","password":"testers"}'
```

##### νμκ°μ μμ²­

```
$ curl -X POST http://192.168.59.100:32667/signup\
   -H 'Content-Type: application/json'\
   -d '{"email":"test@test.com","password":"testers"}'
```

##### make tasks-service

```
$ minikube service tasks-service
|-----------|---------------|-------------|-----------------------------|
| NAMESPACE |     NAME      | TARGET PORT |             URL             |
|-----------|---------------|-------------|-----------------------------|
| default   | tasks-service |        8000 | http://192.168.59.100:30415 |
|-----------|---------------|-------------|-----------------------------|
π  Opening service default/tasks-service in default browser...
```

##### Task μ‘°ν

```
$ curl http://192.168.59.100:30415/tasks\
   -H "Authorization: Bearer abc"
```

##### Task μμ±

```
$ curl -X POST http://192.168.59.100:30415/tasks\
   -H "Content-Type: application/json"\
   -H "Authorization: Bearer abc"\
   -d '{"text":"world","title":"hello"}'
```