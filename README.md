# CI/CD Pipelines

This repo includes two focused pipelines. 

One builds and pushes a Docker image, while the other validates Terraform configuration. Each workflow is scoped to a specific part of the repository and is designed to do one thing clearly.

Both pipelines live in the same repo but are kept separate by design, reflecting how CI and CI/CD are commonly structured in practice.

```
. 
├─ README.md
├─ LICENSE
├─ .gitignore
|
├─ docker-build-push/
│  ├─ Dockerfile
│  ├─ hello.py
│  └─ README.md
|
├─ terraform-checks/
│  ├─ main.tf
│  ├─ provider.tf
│  └─ README.md
|
├─ assets/
│  ├─ docker-build-push.png
│  └─ terraform-ci-checks.png
|
└─ .github/
   └─ workflows/
      ├─ docker-build-push.yaml
      └─ terraform-ci-checks.yaml
```

Each directory represents a focused pipeline with its own code and documentation. 

All GitHub Actions workflows live in `.github/workflows` at the repository root, as required by GitHub Actions.

## Included Pipelines

### Docker Build and Push

A CI/CD pipeline that builds and publishes a Docker image on push. It focuses on:

- Building a container image from a scoped build context
- Tagging and publishing images to Docker Hub
- Authenticating securely using GitHub Actions secrets
- Keeping the workflow explicit and predictable

See [docker-build-push/README.md](docker-build-push/README.md) for details.

### Terraform Validation

A CI pipeline that validates Terraform configuration without applying infrastructure. It focuses on:

- Enforcing consistent formatting with terraform fmt
- Validating configuration using terraform validate
- Catching errors early without requiring cloud credentials
- Keeping infrastructure changes out of CI by design

See [terraform-checks/README.md](terraform-checks/README.md) for details.
