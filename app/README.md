## Running the Project with Docker

This project is set up to run a Node.js application in Docker using the provided `Dockerfile` and `docker-compose.yml` configuration.

### Requirements & Configuration
- **Node.js Version:** The Dockerfile uses Node.js version `22.13.1-slim` (set via the `NODE_VERSION` build argument).
- **Dependencies:** Only `package.json` is present; dependencies are installed with `npm install --production` (no `package-lock.json`).
- **User:** The container runs as a non-root user for security.
- **Environment Variables:**
  - `NODE_ENV=production` (set in the Dockerfile)
  - `NODE_OPTIONS=--max-old-space-size=4096` (set in the Dockerfile)
  - No additional environment variables are required by default. If you need to add any, you can use an `.env` file and uncomment the `env_file` line in the compose file.

### Build and Run Instructions
1. **Build and start the service:**
   ```sh
   docker compose up --build
   ```
   This will build the image using the provided Dockerfile and start the `javascript-app` service.

2. **Accessing the Application:**
   - The app will be available on [http://localhost:3000](http://localhost:3000) (port 3000 is exposed and mapped).

### Ports
- **javascript-app:**
  - Exposes port **3000** (container) → **3000** (host)

### Special Notes
- No external dependencies or special configuration are required beyond what is specified above.
- If you need to provide environment variables, create a `.env` file in the project root and uncomment the `env_file` line in the `docker-compose.yml`.
