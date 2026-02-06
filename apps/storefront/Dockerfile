FROM node:20

WORKDIR /usr/src/app

# Copy root package files
COPY package.json package-lock.json ./

# Copy storefront package file
COPY apps/storefront/package.json ./apps/storefront/

# Install dependencies
RUN npm ci

# Copy storefront source code
COPY apps/storefront ./apps/storefront

# Build the storefront
WORKDIR /usr/src/app/apps/storefront
# Set environment variables for build if needed, though usually better at runtime or build args
ENV NEXT_TELEMETRY_DISABLED 1
RUN npm run build

# Expose the port
EXPOSE 3002

CMD ["npm", "run", "start"]
