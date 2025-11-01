## builder-signing-server

Server for creating builder headers remotely

## Endpoints

- **Health Check**: GET `/` - Returns server status

- **Sign Endpoint**: POST `/sign` - Accepts signing requests with path, method, and body and returns a `BuilderHeaderPayload`

## Prerequisites

- **Node.js**: v18 or higher

## Installation

```bash
# Install dependencies
pnpm install
```

## Docker

### Building the Image

```bash
# Build the Docker image
docker build -t builder-signing-server .
```

### Running the Container

```bash
# Run with environment variables
docker run -d \
  -p 8080:8080 \
  -e POLY_BUILDER_API_KEY=your_api_key \
  -e POLY_BUILDER_SECRET=your_secret \
  -e POLY_BUILDER_PASSPHRASE=your_passphrase \
  -e PORT=8080 \
  -e AUTHORIZATION_TOKEN=your_token \
  --name builder-signing-server \
  builder-signing-server
```

### Using a `.env` File

You can also use a `.env` file with Docker:

```bash
# Run with .env file
docker run -d \
  -p 8080:8080 \
  --env-file .env \
  --name builder-signing-server \
  builder-signing-server
```

**Note**: The container exposes port 8080 by default. Use `-p <host-port>:8080` to map to a different host port (e.g., `-p 3000:8080` to access on port 3000).

## Environment Variables

Create a `.env` file in the root directory using the `.env.example` file as an example:

```env
PORT=3000
POLY_BUILDER_API_KEY=your_api_key
POLY_BUILDER_SECRET=your_secret
POLY_BUILDER_PASSPHRASE=your_passphrase
```

## Project Structure

```
├── src/                 # TypeScript source files
│   ├── app.ts          # Express app configuration
│   ├── server.ts       # Server entry point
│   └── types.ts        # Type definitions
├── dist/               # Compiled JavaScript (generated)
├── coverage/           # Test coverage reports (generated)
├── tests/              # Test files
├── Makefile           # Build configuration
├── tsconfig.json      # TypeScript configuration
└── package.json       # Dependencies and scripts
```
