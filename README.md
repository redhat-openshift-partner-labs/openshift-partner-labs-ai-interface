# Agent UI

A modern chat interface for AI agents built with Next.js, Tailwind CSS, and TypeScript. This template provides a ready-to-use UI for interacting with Agno agents.

<img src="https://github.com/user-attachments/assets/7765fae5-a813-46cb-993b-904af9bc1672" alt="agent-ui" style="border-radius: 10px; width: 100%; max-width: 800px;" />

## Features

- 💬 **Modern Chat Interface**: Clean design with real-time streaming support
- 🧩 **Tool Calls Support**: Visualizes agent tool calls and their results
- 🧠 **Reasoning Steps**: Displays agent reasoning process (when available)
- 📚 **References Support**: Show sources used by the agent
- 🖼️ **Multi-modality Support**: Handles various content types including images, video, and audio
- 🎨 **Customizable UI**: Built with Tailwind CSS for easy styling
- 🧰 **Built with Modern Stack**: Next.js, TypeScript, shadcn/ui, Framer Motion, and more

## Getting Started

### Prerequisites

Before setting up Agent UI, you may want to have an Agno Playground running. If you haven't set up the Agno Playground yet, follow the [official guide](https://agno.link/agent-ui#connect-to-local-agents) to run the Playground locally.

### Installation

### Automatic Installation (Recommended)

```bash
npx create-agent-ui@latest
```

### Manual Installation

1. Clone the repository:

```bash
git clone https://github.com/agno-agi/agent-ui.git
cd agent-ui
```

2. Install dependencies:

```bash
pnpm install
```

3. Start the development server:

```bash
pnpm dev
```

4. Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Docker Support

This project includes Docker support for easy deployment and consistent development environments.

### Running with Docker

#### Quick Start

```bash
# Build the Docker image
podman build -t agent-ui .

# Run the container
podman run -p 3000:3000 agent-ui
```

#### Development with Docker

```bash
# Build development image
podman build -t agent-ui:dev .

# Run with volume mounting for development
podman run -p 3000:3000 -v $(pwd):/app -v /app/node_modules agent-ui:dev
```

#### Docker Compose (Recommended)

Create a `podman-compose.yml` file:

```yaml
version: '3.8'
services:
  agent-ui:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
```

Then run:
```bash
podman-compose up
```

### Docker Configuration

- **Base Image**: Node.js 22 Alpine Linux
- **Multi-stage Build**: Optimized for production deployment
- **Standalone Output**: Uses Next.js standalone mode for minimal image size
- **Security**: Runs as non-root user with proper permissions
- **Port**: Exposes port 3000

### Environment Variables

- `NODE_ENV`: Set to `production` for production builds
- `NEXT_TELEMETRY_DISABLED`: Set to `1` to disable telemetry
- `PORT`: Application port (default: 3000)
- `HOSTNAME`: Bind hostname (default: 0.0.0.0)

## Connecting to an Agent Backend

By default Agent UI connects to `http://localhost:7777`. You can easily change this by hovering over the endpoint URL and clicking the edit option.

The default endpoint works with the standard Agno Playground setup described in the [official documentation](https://agno.link/agent-ui#connect-to-local-agents).

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution guidelines.

## License

This project is licensed under the [MIT License](./LICENSE).
