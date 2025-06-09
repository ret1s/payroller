FROM node:18-alpine

# Install pnpm globally
RUN npm install -g pnpm

WORKDIR /app

# Copy package files first for better Docker layer caching
COPY package.json pnpm-lock.yaml ./

# Install dependencies with frozen lockfile for faster, deterministic builds
RUN pnpm install --frozen-lockfile --prefer-offline

# Copy source code
COPY . .

EXPOSE 5173

# Use pnpm for development
CMD ["pnpm", "run", "dev", "--", "--host", "0.0.0.0"]