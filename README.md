# E-Vote GitOps

Minimal GitOps repository for the E-Vote application. Contains Kubernetes manifests and Argo CD apps to deploy services, databases, and networking for a small on-prem cluster.

## Contents

- `base/` : core Kubernetes manifests (deployments, services, configmaps, volumes).
- `bootstrap/` : Argo CD application manifests used to bootstrap cluster components.
- `overlays/` : environment-specific kustomize overlays (`stage`, `prod`).

## Quick start

1. Install and configure a Kubernetes cluster and a GitOps tool such as Argo CD.
2. Apply the manifests or import this repo into Argo CD.

Example using `kubectl` for the base manifests:

```bash
# apply base manifests
kubectl apply -k base
```

For environment overlays, use:

```bash
# apply stage overlay
kubectl apply -k overlays/stage

# apply prod overlay
kubectl apply -k overlays/prod
```

## Notes

- Services expect a `evote` namespace. Create it if missing: `kubectl create ns evote`.
- This repo includes manifests for Kong ingress, Kafka, Zookeeper, and Postgres instances used by the services.

## Next steps

- Import the repo into Argo CD or wire CI to push to your cluster.
- Review secrets and configuration before deploying to production.

## License

Repository contains infrastructure manifests. License not specified.
