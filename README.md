# Kubernetes-With-MOOC Configuration Repository

This repository contains Kubernetes manifests and configurations for the TodoApp project.

## Structure

```
.
├── base/                      # Base Kubernetes manifests
│   ├── manifests/            # All resource definitions
│   ├── Persistent/           # PVC definitions
│   └── kustomization.yaml    # Base kustomization
├── overlays/
│   ├── staging/              # Staging environment overlay
│   │   └── kustomization.yaml
│   └── production/           # Production environment overlay
│       └── kustomization.yaml
└── argocd/                   # ArgoCD application definitions
    ├── todoapp-staging.yaml
    └── todoapp-production.yaml
```

## Deployment

This repository is automatically updated by CI/CD pipelines from the [Kubernetes-With-MOOC](https://github.com/ShehzadKhuwaja/Kubernetes-With-MOOC) repository.

### Staging
- **Updated on**:  Every commit to `main` branch
- **Namespace**: `staging`
- **Auto-sync**: Enabled

### Production
- **Updated on**: Git tags (v*. *. *)
- **Namespace**: `production`
- **Auto-sync**: Enabled

## ArgoCD Setup

Apply the ArgoCD applications: 

```bash
kubectl apply -f argocd/todoapp-staging.yaml
kubectl apply -f argocd/todoapp-production. yaml
```

## Manual Testing

Test kustomize builds locally: 

```bash
# Staging
kustomize build overlays/staging

# Production
kustomize build overlays/production
```
```