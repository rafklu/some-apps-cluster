# Consul

## Run

Run image as daemon:
`docker run -d --name=dev-consul -p 8500:18500 -e CONSUL_BIND_INTERFACE=eth0 consul`

Run image interactively:
`docker run -it --rm --name=dev-consul -p 8500:18500 -e CONSUL_BIND_INTERFACE=eth0 consul`

## CLI

Put new property:
`consul kv put config/some-demo-app1/data 'consul.app.name: "Some Demo App1 Name"'`

Get property:
`consul kv get config/some-demo-app1/data`


## Useful links
* https://github.com/indrabasak/spring-consul-example/blob/master/client/README.md