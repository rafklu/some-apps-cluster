# Somme apps cluster

## Run docker containers manualy

Create network:
`docker network create some-network`

Start Registry container:
`docker run -d --name registry -p 5000:5000 --restart=always --network some-network registry:2`

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
`docker run -it --rm --name=some-demo-app1 -p 18080:8080 -e SPRING_PROFILES_ACTIVE=docker --network some-network localhost:5000/some-demo-app1`

## Run docker containers using Docker-Compose

Run command:
`docker-compose up`

Put Some Demo App1 properties (described above), then restart Some Demo App1 container using command:
`docker-compose restart some-demo-app1` 

## Useful commands

### List reserved ports by Windows 10
`netsh int ipv4 show excludedportrange protocol=tcp`

## Useful links
* https://www.baeldung.com/spring-cloud-kubernetes
* https://piotrminkowski.com/2019/11/06/microservices-with-spring-boot-spring-cloud-gateway-and-consul-cluster/
* https://docs.docker.com/compose/