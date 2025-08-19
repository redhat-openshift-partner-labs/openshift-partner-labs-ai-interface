# Contributing to Agent UI

Contributions are welcome! Please feel free to submit a Pull Request or raise an issue.

## Development Setup

### Prerequisites

- Node.js 18.0.0 or higher
- pnpm package manager
- Podman (optional, for containerized development)

### Local Development

1. Clone and setup:
```bash
git clone <repository-url>
cd agent-ui
pnpm install
```

2. Start development server:
```bash
pnpm dev
```

### Container Development

For a containerized development environment:

1. Build the container image:
```bash
podman build -t agent-ui:dev .
```

2. Run with development setup:
```bash
podman run -p 3000:3000 agent-ui:dev
```

### Code Quality

Before submitting a PR, ensure your code passes all quality checks:

```bash
# Run all validation checks
pnpm validate

# Individual commands
pnpm lint          # ESLint
pnpm format        # Prettier formatting
pnpm typecheck     # TypeScript checking
pnpm build         # Production build test
```

### Container Best Practices

When working with container-related changes:

1. **Test locally**: Build and run the container image before submitting
2. **Optimize builds**: Keep .dockerignore updated to exclude unnecessary files
3. **Security**: Never include secrets in container images
4. **Size optimization**: Use multi-stage builds and minimal base images

## CI/CD Pipeline

The project uses GitHub Actions for automated continuous integration and deployment:

### Automated Workflows

1. **Code Validation**: Every PR and main branch push triggers:
   - ESLint code quality checks
   - Prettier formatting validation
   - TypeScript type checking
   - Production build verification

2. **Container Image Building**: 
   - **Pull Requests**: Builds container image for validation (no publishing)
   - **Main Branch**: Builds and publishes to Quay.io registry

3. **Container Registry**: Images are published to `quay.io/rhopl/openshift-partner-labs-ai-interface`

### Image Tagging Strategy

Published images include multiple tags:
- `latest`: Always points to the latest main branch
- `main`: Branch-specific tag
- `main-abc1234`: Branch + commit SHA (for traceability)  
- `abc1234`: Short commit SHA

### Required Repository Secrets

For container publishing to work, the following secrets must be configured:

- **`QUAY_USERNAME`**: Quay.io username for authentication
- **`QUAY_TOKEN`**: Quay.io robot token or account password

### CI/CD Best Practices

- All quality checks must pass before container builds
- Container images are only published from the main branch
- Every commit gets a unique tagged image for rollback capability
- Failed builds prevent publishing to maintain image quality

## How to Contribute

1. For bugs and feature requests, please raise a ticket first
2. Fork the repository
3. Create your feature branch (`git checkout -b feature/amazing-feature`)
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

### Submission Guidelines

1. **Code Quality**: All PRs must pass the validation workflow
2. **Container Testing**: If modifying container-related files, test the build locally
3. **Documentation**: Update README.md if adding new container features
4. **CI/CD**: Ensure your changes don't break the container image build process

## Code of Conduct

Please be respectful and considerate of others when contributing to this project.

## Questions?

If you have any questions about contributing, please feel free to reach out to the maintainers.
