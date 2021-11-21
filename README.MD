# Mimic Cloud Provider
A mock cloud provider to simulate the app deployment lifecycle in cloudshell.
Very useful for demo scenarios, or to test configuration management against static infra.

## Usage
- Install 2G cloud provider shell
- Create app
- Set IP of target vm in deployment attributes

## Docker workflow
Docker container can be used as static infra.

Spin up a docker container and configure port forwarding accordingly

```
docker run --rm -it -p 22:2222 -e PUID=1000 -e PGID=1000 -e TZ=Europe/London -e USER_NAME=admin -e USER_PASSWORD=admin -e PASSWORD_ACCESS=true linuxserver/openssh-server
```