# Pishro redis Package

This is a Pishro package that installs and manages **redis** in a Docker Swarm environment.

## Requirements
- Pishro cli is installed.
- Docker Engine with Swarm mode enabled.
- Basic knowledge of Docker and redis configuration.

## Installation
Add the pishro-catalog:

```bash
uv run pishro repo add --url https://github.com/siavashoutadi/pishro-catalog.git pishro-catalog
```

Download the redis package:

```bash
pishro package download --repo pishro-catalog --name redis --destination ./pishro-packages
```

Add custom values:

```bash
editor values.yaml
```

Override the values according to the requirements by adding the following lines to the `values.yaml` file. For example:

```yaml
deploy:
  resources:
    limits:
      cpu: "2"
      memory: "2G"
    requests:
      cpu: "1"
      memory: "1G"

networks:
  - my-network
```

Install the package:

```bash
uv run pishro package install --packages-path ./pishro-packages/ --name redis --override-values-file ./values.yaml
```
