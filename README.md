# README

```bash
brew install fluxcd/tap/flux
```

```bash
export GITHUB_TOKEN=<your-token>
export GITHUB_USER=<your-username>
```

```bash
flux check --pre
```

```bash
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=gitops-infra-repo-example-1 \
  --branch=main \
  --path=./clusters/my-cluster \
  --personal
```

```bash
flux create kustomization podinfo \
  --target-namespace=default \
  --source=flux-system \
  --path="./apps/podinfo/base" \
  --prune=true \
  --interval=5m \
  --export >> ./clusters/my-cluster/apps.yaml
```

```bash
flux reconcile source git flux-system && flux reconcile kustomization flux-system
```

```bash
    diff <(kustomize build apps/podinfo/base) <(kustomize build apps/podinfo/environments/qa)
```
