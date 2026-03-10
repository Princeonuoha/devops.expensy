SECURITY.md
# Security Policy

## Secrets Management

Sensitive configuration values are stored using secure mechanisms:

- GitHub Secrets for CI/CD credentials
- Kubernetes Secrets for application credentials
- ConfigMaps for non-sensitive configuration

Secrets are never committed to the repository.

## Container Security

All services run inside Docker containers.

Images are stored in Docker Hub and pulled during deployment.

Images are built using minimal base images to reduce attack surface.

## Infrastructure Security

The application runs inside Azure Kubernetes Service (AKS).

Security controls include:

- namespace isolation
- Kubernetes RBAC
- private container registries
- restricted service access

## Data Security

Application data is stored in MongoDB.

Redis is used as an in-memory caching layer.

Sensitive data is not stored in plaintext where avoidable.

## CI/CD Security

The CI/CD pipeline uses:

- GitHub Actions
- encrypted repository secrets
- restricted access tokens

Credentials are injected only during pipeline execution.

## Responsible Disclosure

If you discover a security vulnerability, please open an issue or contact the maintainers privately.