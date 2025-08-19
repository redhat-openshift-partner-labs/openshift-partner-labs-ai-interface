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

### Docker Development

For a containerized development environment:

1. Build the Docker image:
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

### Docker Best Practices

When working with Docker-related changes:

1. **Test locally**: Build and run the Docker image before submitting
2. **Optimize builds**: Keep .dockerignore updated to exclude unnecessary files
3. **Security**: Never include secrets in Docker images
4. **Size optimization**: Use multi-stage builds and minimal base images

## How to Contribute

1. For bugs and feature requests, please raise a ticket first
2. Fork the repository
3. Create your feature branch (`git checkout -b feature/amazing-feature`)
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

### Submission Guidelines

1. **Code Quality**: All PRs must pass the validation workflow
2. **Docker Testing**: If modifying Docker-related files, test the build locally
3. **Documentation**: Update README.md if adding new Docker features
4. **CI/CD**: Ensure your changes don't break the container image build process

## Code of Conduct

Please be respectful and considerate of others when contributing to this project.

## Questions?

If you have any questions about contributing, please feel free to reach out to the maintainers.
