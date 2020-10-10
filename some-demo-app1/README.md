# Some Demo App

## Configuration

### Info Endpoint
To display custom information at `https://localhost:8080/actuator/info` without writing code, you can customize it using `info.*` properties:
```
info:
   app.name: "Some Value"
```

### Consul
To read `data` key from consul set in `bootstrap.yaml`:
```
spring:
  cloud:
    consul:
      config:
        format: YAML
```

## Build docker image with app

### Manually
Build artifact:
`mvn clean package`

Build image:
`docker build . --tag some-demo-app1:0.0.1-SNAPSHOT`

Tag image
`docker tag some-demo-app1:0.0.1-SNAPSHOT localhost:5000/some-demo-app1`

Push image to local repository:
`docker push localhost:5000/some-demo-app1`

### Using `dockerfile-maven-plugin`
Run maven command:
`mvn clean deploy -Dmaven.deploy.skip`

## Run
Run image as daemon:
`docker run -d --name=some-demo-app1 -p 18080:8080 localhost:5000/some-demo-app1`

Run image interactively:
`docker run -it --rm --name=some-demo-app1 -p 18080:8080 localhost:5000/some-demo-app1`

## Test
Open https://localhost:8080/actuator/info to check if application is working properly.
Should disply some JSON containg `app.name`.

## Useful Links
* https://cloud.spring.io/spring-cloud-consul/multi/multi_spring-cloud-consul-config.html
* https://www.baeldung.com/spring-cloud-consul
* https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html#production-ready-application-info