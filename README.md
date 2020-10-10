## Windows 10 + WSL2 + Docker

### List reserved ports
`netsh int ipv4 show excludedportrange protocol=tcp`

## Useful links
* https://www.baeldung.com/spring-cloud-kubernetes
* https://piotrminkowski.com/2019/11/06/microservices-with-spring-boot-spring-cloud-gateway-and-consul-cluster/

## Run images manualy

Create network:
`docker network create some-network`

Run images using created network:
`docker run ... --network some-network ...`

docker run -d --name=dev-consul -p 18500:8500 -e CONSUL_BIND_INTERFACE=eth0 --network some-network consul
docker run -it --rm --name=some-demo-app1 -p 18080:8080 --network some-network sample-demo-app1:0.0.1-SNAPSHOT