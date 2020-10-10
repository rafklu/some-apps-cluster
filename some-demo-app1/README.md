# Some Demo App1

## Build image manualy
First build application using maven:
```mvn clean package```

Second build docker image:
```docker build . --tag some-demo-app1:0.0.1-SNAPSHOT```

## Test
Open https://localhost:8080/actuator/info to see if application is working properly.

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

## Useful Links
* https://cloud.spring.io/spring-cloud-consul/multi/multi_spring-cloud-consul-config.html
* https://www.baeldung.com/spring-cloud-consul
* https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html#production-ready-application-info