<p><img src="https://doc.traefik.io/traefik/assets/img/traefikproxy-vertical-logo-color.svg" alt="traefik-logo" title="traefik" align="top" height=205 /></p>

*Traefik is an open-source Edge Router that makes publishing your services a fun and easy experience. It receives requests on behalf of your system and finds out which components are responsible for handling them.*

### General informations

This Ansible role is designed to deploy and configure the Traefik Edge Router on target servers (using pre-built binary).

**Table of Contents**

  - [Roles variables](#role-variables)
  - [Examples](#examples)
  - [Install and use this role](#install-and-use-this-role)

**Supported Platforms**

  - Red Hat Enterprise Linux 8.x/9.x
  - Fedora 37
  - Ubuntu 22.04 *Jammy Jellyfish*
  - Debian 11 *Bullseye*

**References**

  - Traefik : https://traefik.io/

### Role variables

The role variables documentation are available here :

  - [General](docs/variables.md#general)
  - [Global](docs/variables.md#global)
  - [Entrypoints](docs/variables.md#entrypoints)
  - [Providers](docs/variables.md#providers)
  - [Ingress Routes](docs/variables.md#ingress-routes)
  - [Middlewares](docs/variables.md#middlewares)
  - [API](docs/variables.md#api)
  - [Logs](docs/variables.md#logs)
  - [Access Logs](docs/variables.md#access-logs)
  - [Metrics](docs/variables.md#metrics)
  - [Tracing](docs/variables.md#tracing)
  - [Ping](docs/variables.md#ping)

### Examples

You can find some configurations examples :

  - [Manage entrypoints configuration](docs/examples.md#manage-entrypoints-configuration)
  - [Manage providers configuration](docs/examples.md#manage-providers-configuration)
  - [Manage ingress route configuration](docs/examples.md#manage-ingress-route-configuration)
  - [Manage middlewares configuration](docs/examples.md#manage-middlewares-configuration)
  - [Manage metrics backends](docs/examples.md#manage-metrics-backends)
  - [Manage tracing backends](docs/examples.md#manage-tracing-backends)
  - [Manage certificates resolvers](docs/examples.md#manage-certificates-resolvers)
  - [Enable Traefik dashboard (insecure mode)](docs/examples.md#enable-traefik-dashboard-insecure-mode)

### Install and use this role

* Install the role using the command-line :

  ```shell
  $ ansible-galaxy role install git+https://github.com/f-bn/traefik-role.git traefik
  ```

* You can also install the role in your projects using a `requirements.yml` file and `ansible-galaxy` command-line :

  ```YAML
  $ cat requirements.yml
  ---
  roles:
    - name: traefik
      src: https://github.com/f-bn/traefik-role.git
      scm: git
      version: '1.0.0'

  $ ansible-galaxy install-f -r requirements.yml
  ```

* Once the role is installed, you can use it in your playbooks :

  ```yaml
  - name: Deploy
    hosts: traefik-proxy
    roles:
      - role: traefik
  ```
