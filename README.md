# README

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
