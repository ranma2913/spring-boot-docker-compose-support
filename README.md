# spring-boot-docker-compose-support
Spring-Boot Docker Compose Example for local testing

## Upstream Docs

- Docker Compose Feature https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#features.docker-compose
- Docker Compose
  Properties: https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html#appendix.application-properties.docker-compose

## Spring-Cloud Bootstrap

`DockerComposeLifecycleManager#start()` is called once for the bootstrap phase and once for the application phase when
using the spring-cloud-starter-bootstrap dependency.
You have to add
the [Docker Compose Properties](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html#appendix.application-properties.docker-compose)
to the bootstrap.yml file if you need to change behavior during Spring-Cloud Bootstrap.

See [bootstrap.yaml](/src/main/resources/config/bootstrap.yaml)

```yaml
spring:
  docker:
    compose:
      enabled: false # disable during bootstrap phase
logging:
  level:
    org:
      springframework:
        boot:
          docker:
            compose:
              lifecycle: trace
```

You can then enable it in an active profile.
See [application-local.properties](/src/main/resources/config/application-local.properties)

```properties
spring.docker.compose.enabled=true
```
