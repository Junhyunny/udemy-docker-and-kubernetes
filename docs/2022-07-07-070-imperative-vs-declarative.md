## The Imperative vs The Declarative Approach

### 1. Imperative

* kubectl create deplyoment ...
* indiviual commands are executed to trigger certain kubernetes actions
* comparable to using docker run only

### 2. Declarative

* kubectl apply -f config.yml
* A config file is defined and applied to change the desired state
* comparable to using docker compose with compose files
