FROM node:16

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./
RUN npm install
RUN npm install typescript@4.9 --save-dev # Install specific TypeScript version

# Copy the rest of the app
COPY . .

# Expose the app's port
EXPOSE 8080

# Start the app
CMD ["npm", "run", "prod"]
