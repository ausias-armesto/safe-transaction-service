# Safe Transaction Service Chart

This chart packages the Safe transaction service resources. The chart assumes that there is already an existing Postgres, Redis and RabbitMQ instance available and connection attribute should be passed in the values of the Helm Chart

## Parameters

### Common parameters

| Name               | Description                                        | Value |
| ------------------ | -------------------------------------------------- | ----- |
| `nameOverride`     | String to partially override common.names.fullname | `""`  |
| `fullnameOverride` | String to fully override common.names.fullname     | `""`  |

### Installation Parameters

| Name                           | Description                                                      | Value                                 |
| ------------------------------ | ---------------------------------------------------------------- | ------------------------------------- |
| `replicas`                     | Replicas for deployment                                          | `1`                                   |
| `strategy`                     | Strategy for deployment                                          | `Recreate`                            |
| `commonLabels`                 | Labels to add to all related objects                             | `{}`                                  |
| `commonAnnotations`            | Annotations to to all related objects                            | `{}`                                  |
| `nodeSelector`                 | Object containing node selection constraint to deployment        | `{}`                                  |
| `resources`                    | Resource specification to deployment                             | `{}`                                  |
| `tolerations`                  | Tolerations specifications to deployment                         | `[]`                                  |
| `affinity`                     | Affinity specifications to deployment                            | `{}`                                  |
| `image.registry`               | Docker registry to deployment                                    | `registry.hub.docker.com`             |
| `image.repository`             | Docker image repository to deployment                            | `safeglobal/safe-transaction-service` |
| `image.tag`                    | Docker image tag to deployment                                   | `""`                                  |
| `image.pullPolicy`             | Pull policy to deployment as deinfed in                          | `IfNotPresent`                        |
| `service.type`                 | service type                                                     | `ClusterIP`                           |
| `service.ports.number`         | service port number                                              | `8888`                                |
| `service.ports.name`           | service port name                                                | `gunicorn`                            |
| `service.sessionAffinity`      | Control where client requests go, to the same pod or round-robin | `None`                                |
| `persistence.storageClassName` | Storage class name for persisting static files                   | `""`                                  |
| `persistence.size`             | Size of the persistence volume                                   | `100M`                                |

### Configuration Parameters

| Name                                 | Description                                                                                                   | Value                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| `config.secretKey`                   | Transaction Service Secret Key. You should generate a random string of 50+ characters for this value in prod. | `""`                                            |
| `config.refSecretKey`                | Reference to an existing secret containing the following entries: DJANGO_SECRET_KEY                           | `""`                                            |
| `config.debug`                       | Enable debug                                                                                                  | `true`                                          |
| `config.ethL2Network`                | Log Level                                                                                                     | `1`                                             |
| `config.ethereumRpcUrl`              |                                                                                                               | `https://primary.gnosis-chain.rpc.hoprtech.net` |
| `config.django.allowedHosts`         | Allowed hosts                                                                                                 | `*`                                             |
| `config.postgres.secretReferenceKey` | Reference to an existing secret containing the following entries: username, password                          | `""`                                            |
| `config.postgres.username`           | PostgreSQL user                                                                                               | `""`                                            |
| `config.postgres.password`           | PostgreSQL user's password                                                                                    | `""`                                            |
| `config.postgres.database`           | PostgreSQL database name                                                                                      | `safe-transaction`                              |
| `config.postgres.host`               | PostgreSQL server host                                                                                        | `""`                                            |
| `config.postgres.port`               | PostgreSQL server port                                                                                        | `5432`                                          |
| `config.redis.secretReferenceKey`    | Reference to an existing secret containing the following entries: password                                    | `""`                                            |
| `config.redis.password`              | Redis user's password                                                                                         | `""`                                            |
| `config.redis.database`              | Redis database number                                                                                         | `0`                                             |
| `config.redis.host`                  | Redis server host                                                                                             | `""`                                            |
| `config.redis.port`                  | Redis server port                                                                                             | `6379`                                          |
| `config.rabbitmq.secretReferenceKey` | Reference to an existing secret containing the following entries: username, password                          | `""`                                            |
| `config.rabbitmq.username`           | RabbitMQ user                                                                                                 | `""`                                            |
| `config.rabbitmq.password`           | RabbitMQ user's password                                                                                      | `""`                                            |
| `config.rabbitmq.virtualHost`        | RabbitMQ virtual host name                                                                                    | `/`                                             |
| `config.rabbitmq.host`               | RabbitMQ server host                                                                                          | `""`                                            |
