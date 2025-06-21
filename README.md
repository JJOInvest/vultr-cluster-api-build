# vultr-cluster-api-build
GitHub Action to build [vultr-cluster-api-provider](https://github.com/vultr/cluster-api-provider-vultr)

Builds and publishes the [Docker image](#docker-image) containing the cluster API provider, and generates and uploads the [install.yaml](#yaml-for-kubernetes-plugin) file to the release.

## Build instructions
Manually run [Publish installer action](https://github.com/JJOInvest/vultr-cluster-api-build/actions/workflows/build.yml). You can set the tag in .github/workflows/build.yml
```yaml
env:
  REGISTRY: ghcr.io
  tag: 0.1.0
```

## Generated artifacts

### Docker image
Build will be published to organization repository and can be pulled 
```bash
docker pull ghcr.io/jjoinvest/vultr-cluster-api-build:0.1.0
```

### yaml for kubernetes plugin
Build generates an 'install.yaml' file in the release at https://github.com/JJOInvest/vultr-cluster-api-build/releases/download/${tag}/install.yaml

[For example here for 0.1.0](https://github.com/JJOInvest/vultr-cluster-api-build/releases/download/0.1.0/install.yaml)

This file contains all the resources built with Kustomize, which are necessary to install this project without its dependencies.

You should replace 'yourapikey' to VULTR_API_KEY at downloaded file
```yaml
apiVersion: v1
kind: Secret
metadata:
  labels:
    cluster.x-k8s.io/provider: infrastructure-vultr
    cluster.x-k8s.io/v1beta1: v1beta1
  name: capvultr-manager-credentials
  namespace: capvultr-system
stringData:
  apiKey: yourapikey
type: Opaque
```