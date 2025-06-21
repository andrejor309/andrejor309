# syntax=docker/dockerfile:1
ARG NODE_VERSION=22.13.1
FROM node:${NODE_VERSION}-slim AS base
WORKDIR /app

# Install dependencies with cache and bind mounts for deterministic builds
COPY --link package.json ./
# No package-lock.json present, so we use npm install
RUN --mount=type=cache,target=/root/.npm \
    npm install --production

# Copy application source
COPY --link app.js ./

# Security: create and use a non-root user
RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser
USER appuser

ENV NODE_ENV=production
ENV NODE_OPTIONS="--max-old-space-size=4096"
EXPOSE 3000
CMD ["node", "app.js"]
