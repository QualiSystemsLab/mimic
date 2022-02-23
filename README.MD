# Mimic Cloud Provider
A mock cloud provider to simulate the app deployment lifecycle in cloudshell.
This is useful for a mock demo scenario, or to test configuration management scripts during development. 
Test your post deployment scripts without waiting for a real vm deployment.

## Usage
- Install 2G cloud provider shell
- Create cloud provider resource of type "Mimic"
- Create app of type "MimicDeploy", set parent cloud provider resource
- Set IP of target static vm in deployment attributes

## Ansible Workflow setup
- If testing ansible, can set deployment IP as 127.0.0.1 in deployment path to have Ansible linux ES controller ping itself
  - NOTE: must use loopback 127.0.0.1 (localhost string will break ansible driver regex parsing)
- When running Ansible, the mimic must run on same ES as the linux ES. 
  - Can add "Supports Ansible" Execution Server Selector attribute to the mimic shell 
  - OR use default Execution Server Selector attribute and match it to the linux ES value (use "linux" for example)


## Sample Docker workflow
Docker container can be used as target static vm.
Spin up a docker container and configure port forwarding accordingly with this command:
```
docker run --rm -it -p 22:2222 -e PUID=1000 -e PGID=1000 -e TZ=Europe/London -e USER_NAME=admin -e USER_PASSWORD=admin -e PASSWORD_ACCESS=true linuxserver/openssh-server
```