Role variables
--------------

#### General

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_version`                 | `2.9.6`                      | Defines the version of Traefik to install                        |
| `traefik_install_dir`             | `/usr/local/bin`             | Defines the Traefik binary installation directory                |
| `traefik_config_dir`              | `/etc/traefik`               | Defines the Traefik configuration directory                      |
| `traefik_config_static_path`      | `{{ traefik_config_dir }}/traefik.yaml`| Defines the absolute path to the static Traefik configuration file |
| `traefik_config_dynamic_dir`      | `{{ traefik_config_dir }}/dynamic`| Defines the directory where Traefik dynamic configuration files are stored |
| `traefik_binary_archive_url`      | see [defaults](../defaults/main.yml) | Defines the URL where to download the Traefik binary archive |
| `traefik_binary_archive_checksum` | see [defaults](../defaults/main.yml) | Defines the Traefik binary checksum (sha256 checksum)    |
| `traefik_binary_update`           | `false`                      | If set to `true`, force the Traefik binary update                |

#### Global

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_global_checknewversion`  | `false`                      | If set to `true`, periodically check if a new Traefik version has been released |
| `traefik_global_sendanonymoususage`| `false`                     | If set to `true`, periodically send anonymous usage statistics   |

#### Entrypoints

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_entrypoints`             | see [defaults](../defaults/main.yml) | Defines the entrypoints configuration (see [examples](examples.md#manage-entrypoints-configuration)) |


#### Providers

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_providers`               | see [defaults](../defaults/main.yml) | Defines the Traefik providers configuration (see [examples](examples.md#manage-providers-configuration)) |

#### Ingress routes

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_ingress_routes`          | `{}`                         | Defines the ingress routes configuration (see [examples](examples.md#manage-ingress-routes-configuration)) |

#### Middlewares

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_middlewares`             | `{}`                         | Defines the Traefik middlewares configuration (see [examples](examples.md#manage-middlewares-configuration)) |

#### API

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_api_enabled`             | `false`                      | If set to `true`, enable the Traefik API                         |
| `traefik_api_insecure`            | `false`                      | If set to `true`, enable the Traefik API in insecure mode, which means that the API will be available directly on the entrypoint named `traefik`|
| `traefik_api_dashboard`           | `false`                      | If set to `true`, enable the Traefik dashboard                   |
| `traefik_api_debug`               | `false`                      | If set to `true`, enable additional endpoints for debugging and profiling, served under `/debug/`|

#### Logs

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_logs_dir`                | `/var/log/traefik`           | Defines the logs directory where Traefik should write his logs   |
| `traefik_logs_filepath`           | `''`                         | If a path is specified, enable file logging at the given path    |
| `traefik_logs_format`             | `common`                     | Defines the logs format (`common` or `json`)                     |
| `traefik_logs_level`              | `ERROR`                      | Defines the logging level (available: `DEBUG`, `PANIC`, `FATAL`, `ERROR`, `WARN`, and `INFO`) |

#### Access Logs

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_access_logs_enabled`     | `false`                      | If set to `true`, enable access logs                             |
| `traefik_access_logs_filepath`    | `''`                         | If a path is specified, enable file logging at the given path    |
| `traefik_access_logs_format`      | `common`                     | Defines the logs format (`common` or `json`)                     |
| `traefik_access_logs_buffering_size`| `''`                       | If a size is specified, enable log writing in asynchronous mode by buffering logs in memory before writing them to the filesystem |

#### Metrics

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_metrics_enabled`         | `false`                      | If set to `true`, enable metrics backends                        |
| `traefik_metrics_backends`        | `{}`                         | Defines the metrics backends configuration (see [examples](examples.md#manage-metrics-backends)) |

#### Tracing

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_tracing_enabled`         | `false`                      | If set to `true`, enable tracing backends                        |
| `traefik_tracing_backends`        | `{}`                         | Defines the tracing backends configuration (see [examples](examples.md#manage-tracing-backends)) |  

#### Ping

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_ping_enabled`            | `false`                      | If set to `true`, enable the Traefik healthcheck endpoint        |
| `traefik_ping_entrypoint`         | `traefik`                    | Defines the name of the entrypoint used for the Traefik healthcheck endpoint |
| `traefik_ping_manualrouting`      | `false`                      | If set to `true`, disable the default internal router in order to allow one to create a custom router for the `ping@internal` service |
| `traefik_ping_terminating_statuscode`| `503`                     | During the period in which Traefik is gracefully shutting down, the ping handler returns a 503 status code by default. If Traefik is behind e.g. a load-balancer doing health checks (such as the Kubernetes LivenessProbe), another code might be expected as the signal for graceful termination. In which case, the terminatingStatusCode can be used to set the code returned by the ping handler during termination |

#### Certificates Resolvers

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `traefik_cert_resolvers_enabled`  | `false`                      | If set to `true`, allow Traefik certificates resolvers configuration |
| `traefik_cert_resolvers`          | `{}`                         | Defines the certificates resolvers configuration (see [examples](examples.md#manage-certificates-resolvers))  |

[Return to main page](../README.md)
