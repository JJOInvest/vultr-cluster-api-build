# vultr-cluster-api-build
GitHub Action to build [vultr-cluster-api-provider](https://github.com/vultr/cluster-api-provider-vultr)

## Build instructions
Manually run [Publish installer action](https://github.com/JJOInvest/vultr-cluster-api-build/actions/workflows/build.yml). You can set the tag in .github/workflows/build.yml
```yaml
env:
  REGISTRY: ghcr.io
  tag: 0.1.0
```

Build will be published to organization repository and can be pulled 
```bash
docker pull ghcr.io/jjoinvest/vultr-cluster-api-build:0.1.0
```