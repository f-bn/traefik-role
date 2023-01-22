Examples
--------

#### Manage entrypoints configuration

```YAML
traefik_entrypoints:
  web:
    address: ":80"
    http:
      redirections:
        entryPoint:
          to: websecure
          scheme: https
  websecure:
    address: ":443"
    http:
      tls:
        certResolver: leresolver
  metrics:
    address: ":8083"
```

More informations on entrypoints [documentation](https://doc.traefik.io/traefik/routing/entrypoints/).

#### Manage providers configuration

```YAML
traefik_providers:
  file:
    directory: /etc/traefik/dynamic
    watch: true
  docker:
    endpoint: "unix:///var/run/docker.sock"
    useBindPortIP: true
    exposedByDefault: false
```

More informations on providers [documentation](https://doc.traefik.io/traefik/providers/overview/).

#### Manage ingress route configuration

Ingress route is a concept tied to this Ansible role and inspired by the IngressRoute CRD available when deploying Traefik on Kubernetes. The goal is to centralize Routers and Services configuration in a single dedicated file for a specific "route" to a given backend.

**NOTE**: this configuration is only available when using the `file` provider.

```YAML
traefik_ingress_routes:
  - name: myapp-route
    description: Route to myapp backend
    mode: http
    routers:
      myapp-router:
        rule: "Host(`myapp.example.com`)"
        service: myapp-service
        middlewares:
        - 'basicauth-myapp'
    services:
      myapp-service:
        loadBalancer:
          servers:
          - url: "http://10.0.10.10:8080/"
          - url: "http://10.0.10.11:8080/"
        healthCheck:
          path: '/healthz'
          port: 8080
```

#### Manage middlewares configuration

```YAML
traefik_middlewares:
  - name: basicauth-myapp
    description: Add basic auth for myapp access
    mode: http
    type: basicAuth
    options:
      users:
        - "user1:$apr1$H6uskk..."
        - "user2:$apr1$d9hr9H..."
```

More informations on middlewares [documentation](https://doc.traefik.io/traefik/middlewares/overview/).

#### Manage metrics backends

```YAML
traefik_metrics_enabled: true
traefik_metrics_backends:
  prometheus:
    entryPoint: metrics
    addRoutersLabels: true
    addServicesLabels: true
```
More informations on metrics backends [documentation](https://doc.traefik.io/traefik/observability/metrics/overview/).

#### Manage tracing backends

```YAML
traefik_tracing_enabled: true
traefik_tracing_backends:
  jaeger:
    samplingServerURL: http://10.0.10.10:5778/sampling
    samplingType: const
    propagation: jaeger
```

More informations on tracing backends [documentation](https://doc.traefik.io/traefik/observability/tracing/overview/).
