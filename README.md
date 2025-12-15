# Backend Service

This repository contains the backend service for the application, migrated from the original monorepo. It handles API requests, WebSocket connections, and integrates with Twilio and OpenAI.

## Project Structure

- `backend/src`: Source code for the backend server.
- `dist`: Compiled JavaScript output (generated).
- `docs`: Documentation for API, WebSocket, and Voice configuration.
- `storage`: Directory for storing recordings and other runtime artifacts.
- `tests`: Test suite.

## Environment Variables

Copy `.env.example` to `.env` and fill in the required values.

- `PORT`: The port the server listens on (default: 3000).
- `NODE_ENV`: Runtime environment (`development` or `production`).
- `BASE_URL`: The public URL of the backend.
- `CORS_ORIGINS`: Comma-separated allowed origins.
- `STORAGE_ROOT`: Path to the local storage directory (e.g., `storage`).
- `TWILIO_*`: Twilio credentials for voice and SMS.
- `OPENAI_API_KEY`: API key for AI services.

## Getting Started

### Prerequisites

- Node.js (v18+)
- npm

### Installation

```bash
npm install
```

### Running in Development

To start the server in development mode with hot-reloading:

```bash
npm run dev
```

This starts the server using `ts-node-dev` from `backend/src/server.ts`.

### Building for Production

To compile the TypeScript code to JavaScript:

```bash
npm run build
```

The output will be in the `dist/` directory.

### Running in Production

After building, start the server:

```bash
npm start
```

### Running Tests

To run the test suite:

```bash
npm test
```

## Storage

The application requires a storage directory for saving recordings and other files. Ensure the directory specified in `STORAGE_ROOT` exists and is writable. The application works with local filesystem storage.

## API & WebSocket

- **REST API**: The API endpoints are documented in `docs/openapi.yaml`.
- **WebSocket**: WebSocket behavior and events are documented in `docs/websocket.md`.

The backend is designed to work with the standalone frontend repository. Ensure `CORS_ORIGINS` includes the frontend's URL.

## Integration

- **Frontend**: Point the frontend application to `BASE_URL`.
- **Twilio**: Configure the Twilio webhook URL to point to this backend's public URL (e.g., via ngrok during development).
