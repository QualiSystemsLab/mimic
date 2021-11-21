# Mimic Cloud Provider
A mock cloud provider to simulate the app deployment lifecycle in cloudshell.
Very useful for demo scenarios, or to test configuration management against static infra.

## Usage
- Install 2G cloud provider shell
- Create cloud provider resource of type "Mimic"
- Create app of type "MimicDeploy", set parent cloud provider resource
- Set IP of target vm in deployment attributes
    - TIP / Trick: if testing ansible, can set deployment IP as 127.0.0.1 to have controller ping itself

## Docker workflow
Docker container can be used as target static vm.

Spin up a docker container and configure port forwarding accordingly with this command:
```
docker run --rm -it -p 22:2222 -e PUID=1000 -e PGID=1000 -e TZ=Europe/London -e USER_NAME=admin -e USER_PASSWORD=admin -e PASSWORD_ACCESS=true linuxserver/openssh-server
```