## Run docker containers manualy

Create network:
`docker network create some-network`

Start Consul container as daemon with exposed `8500` port at `18500`:
`docker run -d --name=dev-consul -p 18500:8500 -e CONSUL_BIND_INTERFACE=eth0 --network some-network consul`

Then put Some Demo App1 properties to Consul using CLI or GUI at http://localhost:18500/ui/dc1/kv.
### CLI
`consul kv put config/some-demo-app1/data 'consul.app.name: "Some Demo App1 Name"'`

### GUI
Create Key / Value entry named `data` at `config/some-demo-app1/` path, containing `YAML` config:
```
consul.app.name: "Some Demo App1 Name"
```

Lastly start Some Demo App1 container exposing port `8080` at `18080` and using `docker` profile:
`docker run -it --rm --name=some-demo-app1 -p 18080:8080 -e SPRING_PROFILES_ACTIVE=docker --network some-network some-demo-app1:0.0.1-SNAPSHOT`

## Windows 10 + WSL2 + Docker

### List reserved ports
`netsh int ipv4 show excludedportrange protocol=tcp`

## Useful links
* https://www.baeldung.com/spring-cloud-kubernetes
* https://piotrminkowski.com/2019/11/06/microservices-with-spring-boot-spring-cloud-gateway-and-consul-cluster/