# Stage 1: Build the Ionic app
FROM beevelop/ionic:latest AS ionic

# Set the working directory
WORKDIR /usr/src/app

# Copy the package files and install dependencies
COPY package*.json ./
RUN npm ci --legacy-peer-deps --omit=optional

# Copy the rest of the application code
COPY . .

# Set the environment variable for OpenSSL
ENV NODE_OPTIONS=--openssl-legacy-provider

# Build the Ionic app
RUN ionic build

# Stage 2: Serve with NGINX
FROM nginx:alpine

# Copy built app from the build stage to NGINX's HTML directory
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html

# Expose the default NGINX port
EXPOSE 80