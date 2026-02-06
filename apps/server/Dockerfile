FROM node:20

WORKDIR /usr/src/app

# Copy root package files
COPY package.json package-lock.json ./

# Copy server package file
COPY apps/server/package.json ./apps/server/

# Install dependencies
# We use npm ci for a clean install based on lockfile
RUN npm ci

# Copy server source code
COPY apps/server ./apps/server

# Build the server
WORKDIR /usr/src/app/apps/server
RUN npm run build

# Expose the port
EXPOSE 3000

# The command will be overridden by docker-compose for worker vs server
CMD ["npm", "run", "start:server"]
